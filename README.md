# Kalman Filters

## Update
```python
def update(mean1, var1, mean2, var2):
    new_mean = (var2*mean1 + var1*mean2)/(var1 + var2)
    new_var = 1 / (1/var1 + 1/var2)
    return [new_mean, new_var]
```

## Predict

```python
def predict(mean1, var1, mean2, var2):
    new_mean = mean1 + mean2
    new_var = var1 + var2
    return [new_mean, new_var]
```


## Test

```python
# 测量值
measurements = [5., 6., 7., 9., 10.]

# 运动值
motion = [1., 1., 2., 1., 1.]

# 测量不确定性
measurement_sig = 4.

# 运动不确定性
motion_sig = 2.

mu = 0.
sig = 10000.

for i in range(len(measurements)):
    [mu, sig] = update(mu, sig, measurements[i], measurement_sig)
    print('update:  ',   [mu, sig])
    [mu, sig] = predict(mu, sig, motion[i], motion_sig)
    print('predict: ', [mu, sig]) 
```
