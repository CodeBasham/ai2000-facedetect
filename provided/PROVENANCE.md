# Where this data came from

## faces/

Every face here came from a generative model rather than a camera. `make_provided_data.py` read crops from a directory named `a small sample (550 images)`, resized each one, and pasted it onto a generated background.

The corpus depicts no one; it was generated, and GAN output does not correspond to any real person.
Nobody was asked for consent because there is nobody to ask. That is the
reason this corpus exists in this form: the alternatives are corpora
assembled without consent, or corpora collected with consent whose terms
forbid handing them to a class.

`faces.csv` records, for each image, the `group` it belongs to and the
ground-truth box. The box is where the face was **placed**, not where any
detector found it. Ground truth that came out of a detector could not be used
to judge that detector.

### The group column

`group` is apparent size: `near` (200-260 px) or
`far` (90-120 px). It is a capture condition --
how far the subject stood from the camera -- and not a property of a person.
These numbers came from `--sweep`ing this detector against this corpus, not
from a guess; re-run `--sweep` and reset them if the corpus changes again.

Worth stating plainly what this choice costs. The best-known finding about
face detection systems is that they perform worse on darker-skinned and
female faces. These faces carry enough photographic detail that you could
sort them by apparent skin tone yourself and measure a detection rate for
each group. That number would be confounded: a generative model renders
faces only as evenhandedly as its training photographs allowed, so a gap you
found could belong to the detector or to the generator, and nothing in this
package lets you tell which. The size gap avoids that problem, because size
is a property this script imposes during compositing rather than something
the generator produced.

The literature's finding and this corpus's finding are two separate
measurements. Cite the literature for one and your own numbers for the
other, and be clear in the memo about which is which.

## scenes/

Drawn by `make_provided_data.py`. Three object classes -- stop signs, traffic
lights, sports balls -- chosen because a detector trained only on photographs
still recognises drawn versions of them, which is worth noticing on its own.
A drawn vehicle was tried and dropped: it was never detected.

`scenes.csv` holds the placed boxes, same convention as above.

## models/

`yolov8n.pt` and `face_detection_short_range.tflite` ship inside this package
and are loaded by path. Nothing here downloads a model at run time, so grading
does not depend on the network being up, and the version cannot drift under
you between now and December.

`yolov8n.pt` is Ultralytics YOLOv8-nano, AGPL-3.0. The BlazeFace weight is
Google's MediaPipe short-range face detector, Apache-2.0.
