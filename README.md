# READ ME

Example MNIST training using the following tech stack:

* Python 3.10.12
* [Ray](https://www.ray.io/)
* [PyTorch](https://pytorch.org/)
* [PyTorch Lightning](https://www.pytorchlightning.ai/)
* [MLflow](https://mlflow.org/)

## Files

* [mnist.py](./mnist.py). Main training. Example from Ray's [documentation](https://docs.ray.io/en/latest/tune/examples/includes/mlflow_ptl_example.html).
* [requirements.txt](./requirements.txt). Install via: `pip install -r requirements.txt`
* [freeze.txt](./freeze.txt). Resulting run-time environment.

## Fixes

In `ray.tune.examples.mnist_ptl_mini` package, change

```python
self.accuracy = Accuracy()
```

to

```python
self.accuracy = Accuracy(task="multiclass", num_classes=10)
```

## Run

```sh
python mnist.py
```

The experiments will be recorded to MLflow in a local folder, `mlruns` and to Ray Tune in `~/ray_results/tune_mnist`.

Launch MLflow in the launch folder.

```sh
mlflow ui
```
