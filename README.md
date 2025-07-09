# DAViD: Data-efficient and Accurate Vision Models from Synthetic Data

The repo accompanies the ICCV 2025 paper [DAViD: Data-efficient and Accurate Vision Models from Synthetic Data](https://microsoft.github.io/DAViD) and contains instructions for downloading and using the SynthHuman dataset and models described in the paper.

## ⚖️ License
This repository contains components under different licenses:

- The SynthHuman dataset is available for non-commercial use, refer to [TODO.txt]() for details.
- The models and runtime code are released under the permissive [LICENSE-MIT.txt](./LICENSE-MIT.txt).

## 📊 The SynthHuman Dataset

<img src="docs/img/SynthHuman-F.jpg" alt="Face Data" width="33%"/><img src="docs/img/SynthHuman-UB.jpg" alt="Upper Body Data" width="33%"/><img src="docs/img/SynthHuman-FB.jpg" alt="Full Body Data" width="33%"/>

The SynthHuman dataset contains approximately 300,000 images of synthetic humans with ground-truth annotations for foreground alpha masks, absolute depth, surface normals and camera intrinsics. There are approximately 100,000 images for each of three camera scenarios: face, upper-body and full-body. The data is generated using the latest version of our synthetic data generation pipeline, which has been used to create a number of datasets: [Face Synthetics](https://microsoft.github.io/FaceSynthetics/), [SimpleEgo](https://aka.ms/SimpleEgo) and [SynthMoCap](https://aka.ms/SynthMoCap). Ground-truth annotations are per-pixel with perfect accuracy due to the graphics-based rendering pipeline:

<img src="docs/img/GT_annotations.jpg" alt="Face Data" width="50%"/>

### Data Format

The dataset contains TODO samples. Each sample is made up of:

- `rgb_0000000.png` - RGB image
- `alpha_0000000.png` - foreground alpha mask
- `depth_0000000.exr` - absolute z-depth image in cm
- `normal_0000000.exr` - surface normal image (XYZ)
- `cam_0000000.txt` - camera intrinsics (see below)

The camera text file includes the standard intrinsic matrix:

```
f_x 0.0 c_x
0.0 f_y c_y
0.0 0.0 1.0
```

Where `f_x`, and `f_y` are in pixel units.
This can be easily loaded with `np.loadtxt(path_to_camera_txt)`.

### Downloading the Dataset

The dataset is broken in TODO zip files to make downloading easier.
Each zip file is approximately 8.75GB in size and contains 5000 samples.
To download the dataset simply run `download_data.py TARGET_DIRECTORY [--single-sample] [--single-chunk]` which will download and unzip the zips into the target folder.
You can optionally download a single sample or a single chunk to quickly take a look at the data.

### Dataset License
The SynthHuman dataset is licensed under the [CDLA-2.0  license](https://cdla.dev/permissive-2-0/).
The download script and other code is licensed under the [LICENSE-MIT.txt](./LICENSE-MIT.txt).

## 🔓 Released Models

We release models for the following tasks:
<table>
  <thead>
    <tr>
      <th>Task</th>
      <th>Version</th>
      <th>ONNX Model</th>
      <th>Model Card</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">Soft Foreground Segmentation</td>
      <td>Base</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/foreground-segmentation-model-vitb16_384.onnx">Download</a></td>
      <td rowspan="2"><a href="./model_cards/soft_foreground_segmentation_model.md">Model Card</a></td>
    </tr>
    <tr>
      <td>Large</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/foreground-segmentation-model-vitl16_384.onnx">Download</a></td>
    </tr>
    <tr>
      <td rowspan="2">Relative Depth Estimation</td>
      <td>Base</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/depth-model-vitb16_384.onnx">Download</a></td>
      <td rowspan="2"><a href="./model_cards/depth_model.md">Model Card</a></td>
    </tr>
    <tr>
      <td>Large</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/depth-model-vitl16_384.onnx">Download</a></td>
    </tr>
    <tr>
      <td rowspan="2">Surface Normal Estimation</td>
      <td>Base</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/normal-model-vitb16_384.onnx">Download</a></td>
      <td rowspan="2"><a href="./model_cards/surface_normal_model.md">Model Card</a></td>
    </tr>
    <tr>
      <td>Large</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/normal-model-vitl16_384.onnx">Download</a></td>
    </tr>
    <tr>
      <td rowspan="1">Multi-Task Model</td>
            <td>Large</td>
      <td><a href="https://facesyntheticspubwedata.z6.web.core.windows.net/iccv-2025/models/multi-task-model-vitl16_384.onnx">Download</a></td>
      <td rowspan="1"><a href="./model_cards/multi_task_model.md">Model Card</a></td>
    </tr>
  </tbody>
</table>


### Model License

DAViD models, and codes are licensed under the [LICENSE-MIT.txt](./LICENSE-MIT.txt).

## 📖 Citation

If you use the SynthHuman Dataset or any of the DAViD models in your research, please cite the following:

```bibtex
@inproceedings{saleh2025david,
    title={{DAViD}: Data-efficient and Accurate Vision Models from Synthetic Data},
    author={Saleh, Fatemeh and Aliakbarian, Sadegh and Hewitt, Charlie and Petikam, Lohit and Xiao, Xian and Criminisi, Antonio and Cashman, Thomas J. and Baltru{\v{s}}aitis, Tadas},
    booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
    year={2025},
    month={October}
}
```
