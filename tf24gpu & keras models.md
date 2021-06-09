### install tensorflow-gpu 2.4

1. create new anaconda environment, I choose python 3.7
2. install cuda: `conda install cudatoolkit=11.0`
3. update GPU driver from Nvidia website, version > 450.x
4. download cuDNN 8.0, add its bin folder to environment path
5. install tensorflow: `pip install tensorflow-gpu==2.4.0`
