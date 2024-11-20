# How to install in 2024

Installing the dependecies as of 2024 using the original requirements has some problems.
This is how I managed to do it:


```bash
conda create --name fewshot python=3.9
conda activate fewshot
mamba install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
mamba install cmake
mamba install habitat-sim headless -c conda-forge -c aihabitat
mamba install pillow
pip3 install -r requirements_noversion.txt
mamba update matplotlib
```

Install habitat-lab from source (not to be confused with habitat-sim)
(Clone this repo in another directory.)
```bash
git clone --branch stable https://github.com/facebookresearch/habitat-lab.git
cd habitat-lab
pip install -e habitat-lab  # install habitat_lab
```

Then run a quick inference to see if it works:
```bash
CUDA_VISIBLE_DEVICES=0 python3 main.py --exp-config rir_rendering/config/test/uniform_context_sampler.yaml --model-dir runs_eval/fs_rir --run-type eval EVAL_CKPT_PATH_DIR runs_eval/fs_rir/data/seen_eval_best_ckpt.pth NUM_PROCESSES 1
```

UPDATE: So far it is not working.
