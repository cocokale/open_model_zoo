# handwritten-japanese-recognition-0001

## Use Case and High-Level Description

This is a network for handwritten japanese text recognition scenario. It consists of VGG16-like backbone, reshape layer and a fully connected layer.
The network is able to recognize japanese text (characters included in [Kondate](http://web.tuat.ac.jp/~nakagawa/database/en/kondate_about.html) dataset).

## Example

![](./test.png) -> 菊池朋子

## Specification

| Metric                                         | Value              |
|------------------------------------------------|--------------------|
| Accuracy on the test set of Kondate            | 97.39%             |
| Source framework                               | PyTorch\*          |


## Accuracy Values

This demo adopts [label error rate](https://dl.acm.org/doi/abs/10.1145/1143844.1143891) as the metric for accuracy.

## Inputs

Shape: [1x1x96x2000] - An input image in the format [BxCxHxW],
where:
  - B - batch size
  - C - number of channels
  - H - image height
  - W - image width

Note that the source image should be converted to grayscale, resized to spefic height (such as 96) while keeping aspect ratio, normalized to [-1, 1] and right bottom padded

## Outputs
The net outputs a blob with the shape [186, 1, 1161] in the format [WxBxL],
where:
  - W - output sequence length
  - B - batch size
  - L - confidence distribution across the supported symbols in [Kondate](http://web.tuat.ac.jp/~nakagawa/database/en/kondate_about.html)

The network output can be decoded by CTC Greedy Decoder



## Legal Information
[*] Other names and brands may be claimed as the property of others.