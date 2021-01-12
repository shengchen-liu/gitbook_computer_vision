# Boundary Issues

## Clipping

Treats the non-existent pixels as black.

## Wrapping

Uses the opposite edge of the image to continue the edge.  It was intended for periodic functions and is useful for seamless images, but looks noticeably bad for non-seamless images.

## Extending

Copies a chunk of the edge to fit the filter kernel.

## Reflecting

Copies a chunk of the edge like the previous method, but it mirrors the edge like a reflection.