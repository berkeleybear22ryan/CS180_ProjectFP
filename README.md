
# Final Project CS180 Ryan Nader
### github: https://github.com/berkeleybear22ryan/CS180_ProjectFP</p>
### website: https://berkeleybear22ryan.github.io/CS180_ProjectFP/</p>
## Repository Structure

- `./code/code002.ipynb`: Contains code and instructions for Part 1 of the project, focusing on fitting a neural field to a 2D image.
- `./code/code005.ipynb`: Contains code for Part 2, which extends the approach to multi-view images and fits a full Neural Radiance Field.
- `./images/`: Contains a variety of images referenced in the report, including training results, PSNR plots, and hyperparameter tuning visuals.
- `./video/`: Contains sample videos, including novel view renderings produced after training the NeRF.

All the code assumes access to a GPU runtime for efficient training and rendering.

## Part 1: Fit a Neural Field to a 2D Image

**What I Did:**
- Implemented a basic neural field model with positional encoding and an MLP.
- Trained on a single 2D image, experimenting with different hyperparameters such as hidden layer sizes, number of frequencies for positional encoding, and learning rates.
- Visualized the training process by plotting the predicted images across iterations and creating PSNR vs. iteration curves.

**Deliverables:**
1. **Detailed Model Architecture & PSNR Plot:**  
   I documented the model’s architecture, highlighting the positional encoding and the MLP layers. I included a PSNR plot showing how training progressed over iterations.
2. **Visualizing the Training Process:**  
   I saved snapshots of the predicted images at various steps to show how the model’s reconstruction quality improved over time.
3. **Running on a Different Image:**  
   I applied the same setup to another image, produced a new PSNR curve, and visualized training progress again.
4. **Hyperparameter Tuning Results:**  
   I varied key parameters (like the number of frequencies, learning rate, and hidden dimensions) and reported their effect on the PSNR and final reconstruction quality.

## Part 2: Fit a Neural Radiance Field from Multi-view Images

**What I Did:**
- Extended the approach to a full NeRF pipeline using multi-view images and camera-to-world transformations.
- Implemented functions to transform coordinates between spaces, sample rays from multiple images, and discretize rays into 3D points.
- Validated the ray sampling by visualizing cameras, rays, and sampled points in 3D using Viser. Initially, I plotted rays from all images together, and then I focused on rays from a single camera for better debugging.

**Deliverables:**
1. **Implementation Explanation (2.1):**  
   I described how each part (transforming coordinates, pixel-to-camera and pixel-to-ray calculations, sampling rays, etc.) was implemented.
2. **Rays & Samples Visualization (2.2):**  
   I plotted a set of rays and their sampled points, along with camera frustums, to confirm correct data loading and ray generation.
    - **First Visualization:** Showed all cameras and rays together, providing a global overview.
    - **Second Visualization:** Focused on rays from a single image, ensuring that rays remain inside the camera frustum and enabling easier debugging.
3. **Training Process & PSNR Curve (2.3):**  
   I showed predicted images across training iterations and plotted the PSNR on the validation set (6 images) over time. This demonstrated the model’s improvement and stability in multi-view scenarios.
4. **Novel View Rendering (2.4):**  
   After training the NeRF, I rendered a novel view trajectory (using `c2ws_test`) to produce a spherical rendering video of the Lego scene. The results matched the reference expectation, achieving above 23 PSNR after about 1000 iterations.

## Bells & Whistles (Extra Credit)

I took on extra enhancements to boost the NeRF’s performance:
- **Improving PSNR to 30+:**  
  I deepened and widened the MLP architecture, increased positional encoding frequencies, and introduced better sampling strategies. After these changes, the network reached around 32 PSNR.
- **Additional Post-processing (Denoising & Sharpening):**  
  After achieving high-quality reconstructions, I applied denoising and sharpening to further improve the visual quality of rendered novel views.

## How to Run

1. **Environment Setup:**  
   Ensure you have `torch`, `numpy`, and `imageio` installed. A GPU is highly recommended. For Viser visualizations, run `pip install viser`.

2. **Running Part 1:**  
   Open `./code/code002.ipynb` in a GPU-enabled environment and follow the instructions.

3. **Running Part 2:**  
   Open `./code/code005.ipynb` similarly. Follow the instructions, run through the cells, and visualize the outputs and metrics.

4. **Viewing Results:**  
   Check the `./images/` directory for saved images and curves. Check `./video/` for rendered novel-view videos.