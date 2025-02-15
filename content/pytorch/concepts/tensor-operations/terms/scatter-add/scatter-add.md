---
Title: '.scatter_add_()'
Description: 'Accumulates values into a tensor along specified dimensions using indices.'
Subjects:
  - 'Data Science'
  - 'AI'
Tags:
  - 'Tensor'
  - 'PyTorch'
  - 'Deep Learning'
  - 'Neural Networks'
CatalogContent:
  - 'intro-to-py-torch-and-neural-networks'
  - 'paths/machine-learning'
---

The **`.scatter_add_()`** function in PyTorch is an in-place operation used to accumulate values from a source tensor into a destination tensor along specified dimensions, based on given indices. It is commonly utilized in scenarios like distributed computations, weighted aggregations, and custom deep-learning layers.

## Syntax

```pseudo
Tensor.scatter_add_(dim, index, src)
```

- `dim`: The dimension along which the values will be scattered and accumulated.
- `index`: A tensor containing the indices of the elements to which the values from the source tensor will be added.
- `src`: The source tensor containing the values to be added to the input tensor.

The function directly updates the input tensor by adding values from the `src` tensor according to the specified indices.

## Example

### Accumulating values in a 2D tensor

In the example below, the code demonstrates how to accumulate values from a source tensor into a destination tensor along a specified dimension using the `.scatter_add_()` function in PyTorch:

```py
import torch

# Create a destination tensor
input_tensor = torch.zeros(3, 3, dtype=torch.float32)

# Source tensor
src = torch.tensor([[1, 2, 3],
                    [4, 5, 6]], dtype=torch.float32)

# Indices (dtype should be long for indices)
index = torch.tensor([[0, 1, 2],
                      [2, 0, 1]], dtype=torch.long)

# Perform in-place scatter_add_
input_tensor.scatter_add_(dim=1, index=index, src=src)

# Print the result
print(input_tensor)
```

The following output will be generated by the above code:

```shell
tensor([[1., 2., 3.],
        [5., 6., 4.],
        [0., 0., 0.]])
```

### Accumulating values in a 3D tensor

In the example below, the code demonstrates how to accumulate values from a source tensor into a 3D destination tensor along a specified dimension using the `.scatter_add_()` function in PyTorch:

```py
import torch

# Create a destination tensor
input_tensor = torch.zeros(2, 2, 3)

# Source tensor
src = torch.tensor([[[1, 2, 3], [4, 5, 6]],
                    [[7, 8, 9], [10, 11, 12]]], dtype=torch.float32)

# Indices (dtype should be long for indices)
index = torch.tensor([[[0, 1, 2], [2, 0, 1]],
                      [[1, 0, 2], [2, 1, 0]]], dtype=torch.long)

# Perform in-place scatter_add_ along dimension 2
input_tensor.scatter_add_(dim=2, index=index, src=src)

# Print the result
print(input_tensor)
```

The output of the above code will be:

```shell
tensor([[[1., 2., 3.],
         [5., 6., 4.]],

        [[8., 7., 9.],
         [12., 10., 11.]]])
```
