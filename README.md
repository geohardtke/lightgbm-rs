![crates.io](https://img.shields.io/crates/v/lightgbm2.svg)

# lightgbm2-rs
A [Microsoft's LightGBM](https://github.com/microsoft/LightGBM) Rust binding


# Why this tool

This tool is based on the work of `@vaaaaanquish`, that unfortunatelly, can't be used in actual linux distributions or recent rust version.

As a Data Scientist who uses LightGBM, I wissh to deploy, and possible train in rust, but as a Machine Learning engineer I wish to load model and data from cloud object storage, what is not possible from the Cpp distribution.

## To use, just add the package to `Cargo.toml`:

```shell
cargo add lightgbm2
```

There are some examples in [`examples` folder](https://github.com/andreclaudino/lightgbm-rs/tree/main/examples), like this one, adapted from `@vaaaaanquish`:

```shell
extern crate serde_json;
use lightgbm::{Dataset, Booster};
use serde_json::json;

let data = vec![vec![1.0, 0.1, 0.2, 0.1],
               vec![0.7, 0.4, 0.5, 0.1],
               vec![0.9, 0.8, 0.5, 0.1],
               vec![0.2, 0.2, 0.8, 0.7],
               vec![0.1, 0.7, 1.0, 0.9]];
let label = vec![0.0, 0.0, 0.0, 1.0, 1.0];
let dataset = Dataset::from_mat(data, label).unwrap();
let params = json!{
   {
        "num_iterations": 3,
        "objective": "binary",
        "metric": "auc"
    }
};
let bst = Booster::train(dataset, &params).unwrap();
```

# Contributions

Contributions are welcome, just make a pull request. No rules other then keep current tests passing, add new tests for new changes and follow good coding practices, the best you can.
