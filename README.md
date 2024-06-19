创建anaconda虚拟环境 python版本为3.9.12
```
conda create -n fasternet python=3.9.12 -y
conda activate fasternet
```
下载代码文件 配置环境
```
git clone https://github.com/JierunChen/FasterNet
cd FasterNet/
pip install -r requirements.txt #txt文件包含下载url 要求cu113版本的torch
```
#另需numpy版本小于2.0，cuda113对应torch1.11版本  
启动命令
```
python train_test.py -g 0,1,2,3,4,5,6,7 --num_nodes 1 -n 4 -b 4096 -e 2000 \ #适当降低参数 单gpu是 -g 1
--data_dir ../../data/imagenet --pin_memory --wandb_project_name fasternet \ #配置数据集路径
--model_ckpt_dir ./model_ckpt/$(date +'%Y%m%d_%H%M%S') --cfg cfg/fasternet_t0.yaml #检查点路径和模型路径
```
