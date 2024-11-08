## Usage

### Classification

```python
if __name__ == '__main__':
    interpolation = T.InterpolationMode.BILINEAR

    ct = ClassificationTransform()
    ct.add_random_resized_crop((255, 255)) \
        .add_random_horizontal_flip(0.5) \
        .add_random_vertical_flip(0.5) \
        .add_rand_augment(interpolation=interpolation) \
        .add_augmix(interpolation=interpolation) \
        .add_auto_augment(interpolation=interpolation) \
        .add_color_jitter(0.4, 0.4, 0.7, 0.015) \
        .add_to_tensor() \
        .add_normalize() \
        .add_random_erasing(0.4)

    width, height = 416, 416
    random_data = np.random.randint(0, 256, (height, width, 3), dtype=np.uint8)
    image = Image.fromarray(random_data, 'RGB')
    out = ct(image)
```

### Detection

```python
if __name__ == '__main__':
    dt = DetectionTransform()
    dt.add_resize((224, 224)) \
        .add_random_hsv() \
        .add_random_vertical_flip(0.5) \
        .add_random_horizontal_flip(0.5) \
        .add_to_tensor() \
        .add_normalize()

    width, height = 416, 416
    image = np.random.randint(0, 256, (height, width, 3), dtype=np.uint8)
    label = image
    data = (image, label)
    output = dt(data)
```

### Segmentation
```python
if __name__ == '__main__':
    dt = Segmentation()
    dt.add_resize((224, 224)) \
        .add_random_hsv() \
        .add_random_vertical_flip(0.5) \
        .add_random_horizontal_flip(0.5) \
        .add_to_tensor() \
        .add_normalize()

    width, height = 416, 416
    image = np.random.randint(0, 256, (height, width, 3), dtype=np.uint8)
    label = image
    data = (image, label)
    output = dt(data)
```
