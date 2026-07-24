---
author: Mindusting
corrected: false
headerFile: false
tags:
  - Programming
  - Python
title: Manejo de imágenes en Python
---

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

```python
from PIL import Image
import io


def image_transformer(
    image_bytes:  bytes,
    max_size:     int | None = None,
    image_format: str | None = None
    ) -> bytes:

    image = Image.open(io.BytesIO(image_bytes))
    original_format = image.format

    grow_factor: float = 1.0
    if max_size:
        grow_factor = max_size / max(image.width, image.height)

    new_proportions = (
        int(image.width  * grow_factor),
        int(image.height * grow_factor)
    )

    scaled_image = image.resize(new_proportions)

    new_image_bytes = io.BytesIO()

    scaled_image.save(
        new_image_bytes,
        format=image_format or original_format
    )
    return new_image_bytes.getvalue()
```

```python
import numpy as np


def print_image_array(array: np.ndarray, output = None) -> None:
    height = array.shape[0]
    width  = array.shape[1]

    color_format: str = "\033[38;2;{};{};{}m\033[48;2;{};{};{}m▄"

    for y_index in range(0, height, 2):
        for x_index in range(width):
            bg_char_index: int = y_index + 1
            print(
                color_format.format(
                    array[bg_char_index, x_index, 0],
                    array[bg_char_index, x_index, 1],
                    array[bg_char_index, x_index, 2],
                    array[y_index, x_index, 0],
                    array[y_index, x_index, 1],
                    array[y_index, x_index, 2]
                ),
                end="",
                file=output,
                flush=False
            )
        print("\033[0m", file=output)
    print("\033[0m", end="", file=output)
```
