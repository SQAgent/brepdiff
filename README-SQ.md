# 环境创建

```bash
git clone https://github.com/brepdiff/brepdiff.git  
cd brepdiff  

conda create -n brepdiff python=3.9  
conda activate brepdiff

pip uninstall numpy  
pip install numpy==1.23.5

pip install torch==2.2.2 torchvision==0.17.2 --index-url https://download.pytorch.org/whl/cu118  
pip install torch-cluster -f https://data.pyg.org/whl/torch-2.2.0+cu118.html  
pip install torch-scatter -f https://data.pyg.org/whl/torch-2.2.0+cu118.html  
pip install dgl -f https://data.dgl.ai/wheels/torch-2.2/cu118/repo.html

pip install -r requirements.txt  
pip install -e .

conda install -c conda-forge pythonocc-core=7.8.1=novtk_h5981d98_102

cd deps/PoissonRecon  
make poissonrecon  
cd ../..  
ln -s deps/PoissonRecon/Bin/Linux/PoissonRecon ./psr

cd deps/PyMesh  
export PYMESH_PATH=`pwd`  
pip install -r python/requirements.txt  
python ./setup.py build  
python ./setup.py install --user  
python -c "import pymesh; pymesh.test()"

wget https://download.blender.org/release/Blender3.4/blender-3.4.0-linux-x64.tar.xz  
tar -xvf blender-3.4.0-linux-x64.tar.xz  
ln -sr ./blender-3.4.0-linux-x64/blender ./blender  
rm -rf blender-3.4.0-linux-x64.tar.xz
```


```bash
# 自行安装子模块
git submodule update --init --recursive  
# docker 
docker build -t brepdiff .
```
