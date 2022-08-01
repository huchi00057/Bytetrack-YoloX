Download ByteTrack Github Resources (Git：ifzhand/ByteTrack)
====
🔗 https://github.com/ifzhang/ByteTrack

[![Image from Gyazo](https://i.gyazo.com/7d920310b4e9e5d0f0376ddce9818449.gif)](https://gyazo.com/7d920310b4e9e5d0f0376ddce9818449)

Amend the code in set.py
====
Near 50 lines in set.py

Just add **encoding='utf-8'** behind "r" .

![image](https://user-images.githubusercontent.com/46515944/182101075-729f47f1-e8ba-4de9-ba74-1475db8bda47.png)

then enter the following in prompt

    python setup.py develop
    
After finished, it would be like that.

![image](https://user-images.githubusercontent.com/46515944/182101718-16a2bbb5-a56a-4735-b9ab-ea2ed35eaaf3.png)


Install requirements
====
    pip install cython
    pip install -e git+https://github.com/samson-wang/cython_bbox.git#egg=cython-bbox
    pip install pycocotools
    pip install -r requirements.txt

⚠ If you would run Bytetrack in GPU, plz do more step as following. ⚠

Visit the Official Pytorch to get the cmd to install pytorch of CUDA.

🔗 https://pytorch.org/get-started/locally/

![image](https://user-images.githubusercontent.com/46515944/182102313-f92798b8-14db-4227-880c-cb1d1cff049e.png)

    nvidia-smi
PS. If you're sure about CUDA version, you can check it in this cmd.

![image](https://user-images.githubusercontent.com/46515944/182102841-4ee2c34c-a5c2-462c-a8e0-83f555c18f53.png)



