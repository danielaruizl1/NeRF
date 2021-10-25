# NeRF-Homework
## General Overview
First of all you will be running the [NeRF](https://arxiv.org/pdf/2003.08934.pdf) (Neural Radiance Fields) architecture, after completing certain parts of the code. Then, you will be running a pretrained [D-NeRF](https://arxiv.org/pdf/2008.02268.pdf) architecture for a predetermined dataset. We expect you to complete these tasks in order and answer the questions in the report in the respective order as well. For the report please use the text editor and the column formatting of your preference. When uploading it, please do it as a PDF with the following name: `lastname_NeRF_code`. All of these methods are very recent so we expect you to have a lot of fun and learn a lot using them ! 
# NeRF
## Part 0: Installation
After cloning the repository, run the folowwing lines of code (you will be working in the pytorch environment): 
```
cd NeRF
conda activate pytorch
pip install -r requirements.txt
```
## Part 1: Completing the code (2.5 pts)
In this section you will be completing the code according to the explanations given in class. We marked the parts of the code you must fill in with "TODO"s. Most of them have hints in the code itself. Please, after doing a "TODO" section, exchange the word "TODO" to "DONE" so that we can examine your code easier during evaluation. 

Now we present a list of the TODO's you have to complete in their respective order and the file in which they are located (Location).

TODO 1 : Define K as the camera parameters matrix. Location: run_nerf.py  

TODO 2 : Report the functionality of get_embedder. Location: run_nerf.py  

TODO 3 : Discuss: Why do we call the function get_embedder again? How did the parameters vary this time? Relate your answer to the NeRF paper. Location: run_nerf.py  

TODO 4 : Complete the None´s to instantiate the fully connected network of NeRF. Location: run_nerf_helpers.py. In your report justify the modifications you made.  

TODO 5 : Complete the None´s to instantiate the fully connected network of NeRF. Location: run_nerf_helpers.py. In your report justify the modifications you made.  

TODO 6 : Complete the fine network parameters according to the Coarse implementation. Location: run_nerf.py  

TODO 7 : Complete the optimizers parameters (learning rate, beta_1, beta_2). Answer: What is the role of these betas in the Adam optimizer? Location: run_nerf.py  

Finally, answer in which Color Space are the inputs of the neural network. Why do you think this Color space is used? Discuss about its importance. In the load_blender.py (load_blender_data function) you will find a hint.

## Part 2: Training NeRF (1 pt)

You will train a low-res (due to computational resources) `lego` NeRF in the following way:
```
CUDA_VISIBLE_DEVICES=x taskset -c n-m python run_nerf.py --config configs/lego.txt
```
After training for 50k iterations (~3-4 hours on a single GPU), you can find the resulting video at `logs/lego_test/lego_test_spiral_50000_rgb.mp4`.

<p align="center">
  <img src="https://user-images.githubusercontent.com/7057863/78473103-9353b300-7770-11ea-98ed-6ba2d877b62c.gif" />
</p>

In your report discuss about the result you obtained. Compare the PSNR you obtained with the one in the NeRF paper.

## Bonus (0.5 pt)
For the bonus vary a hyperparameter of the NeRF architecture in the argparser (e.g. netdepth, netwidth, netdepth_fine, netwidth_fine, N_importance (it would be interesting to increase it since it was 0 for the low resulation previously implemented, however, it would require much more rendering time), multires (you already discussed about this hyperparameter), multires_view (you already discussed about this hyperparameter), etc). Discuss about the result you obtained compared to the baseline.  

## D-NeRF (1.5 pts)

<p align="center">
<img src='https://www.albertpumarola.com/images/2021/D-NeRF/teaser2.gif' >
</p>

## Part 0: Discussion
In your report discuss about how should the implementation of the D-NeRF **architecture** should vary in comparison to the NeRF one (previous section). Rely on the papers and the code provided.

## Part 1: Installation
Run the following commands:

```
cd d-NeRF
conda create -n dnerf python=3.6
conda activate dnerf
conda install pytorch torchvision cudatoolkit=10.2 -c pytorch
pip install -r requirements.txt
cd torchsearchsorted
pip install .
cd ..
```

## Part 2: Render Video
To render the video run the following lines of code,
```
conda activate dnerf
export PYTHONPATH='path/to/D-NeRF'
export CUDA_VISIBLE_DEVICES=x
python run_dnerf.py --config configs/mutant.txt
```
You can exchange the *mutant.txt* for the .txt file of your preference. Choose the object you would like to render and exists in the configs folder.

## Part 3: Test
Now run the test over your rendered output with the following code,
```
python run_dnerf.py --config configs/mutant.txt --render_only --render_test
```
This command will run the `mutant` experiment. Remember to exchange this .txt if you chose another dataset. When finished, results are saved to `./logs/mutant/renderonly_test_799999`
## Part 4: Metrics
Finally, to quantitatively evaluate model run the `metrics.py` file. Report your results in the report and discuss about it. 

**Please, push your _.mp4_ files to the repository so that we can observe your qualitative results.**


