L4 and L5 notes, plus memo talking points (from Aen)

L4 - the app (app.py)
- Mode: blur. Finds each face and blurs only inside the face box.
- Returns a NEW copy of the picture. The original is never changed, nothing is saved.
- Report it gives back: how many faces it blurred, the mode, and how much of the picture was face.
- Boxes that run off the edge of the picture get trimmed to fit.
- count and overlay modes also work (draws an outline box instead of blurring).

L5 - who it is worse for (audit.py)
- Test set: 550 AI-generated faces, two groups by face size.
- Near (face 200-260 px): found 275 of 275 = 100%
- Far (face 90-120 px): found 19 of 275 = 6.9%
- Worst group: far.
- A "hit" = it found any face in the picture (we don't check the box location, per the assignment).

Memo talking points from L4 and L5

Section 1 (what it does):
- It finds WHERE a face is, never WHO it is. It gets a box and a score, nothing about identity.
- It doesn't store faces or names. It just hands back a blurred copy.

Section 3 (what we measured, what we didn't):
- Our gap is face SIZE / distance from the camera: 100% near vs 6.9% far.
- That gap was built into the test data on purpose (see provided/PROVENANCE.md). It is NOT about skin tone or gender.
- The faces are AI-generated, so we can't test skin tone or gender: any gap could come from the image generator, not the detector.
- Cite Buolamwini and Gebru, "Gender Shades" (2018) for the skin tone / gender finding, and say plainly we did NOT test it.
- Don't sort our faces by skin tone and report it as a detector result. The instructions call that the most expensive mistake.

Section 4 (rules before real use):
- A blur tool fails the people far from the camera: their faces stay unblurred. Privacy breaks in the background.
- So before real use: test it at the real camera distances, and decide what happens to a frame where a face was missed (for example, don't publish it, or blur the whole frame).
