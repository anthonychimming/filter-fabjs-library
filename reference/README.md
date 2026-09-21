# Approved reference image

No production reference image has been approved or included yet. Do not use test
fixture images as production artwork. A maintainer must supply and approve a
project-owned or safely licensed image, exactly 512 × 512, and record its source,
licence and approval here before authoring production packages.

The reference should cover dark/light and saturated/neutral colours, tonal range,
gradients, hard/soft edges, texture and organic/geometric detail where practical.

To produce a sample, load this image in Filter FabJS, import the canonical source
JSON, reset to its authored defaults, render, then export a portable PNG with
embedded FilterFabJS metadata. Confirm the export is 512 × 512 and save it under
the new revisioned filename. Export the matching native source JSON too.

CI validates dimensions and the embedded document; it cannot certify that the
visible pixels came from this reference image. A maintainer reviews that manually.
There is no automated effect rendering in CI.
