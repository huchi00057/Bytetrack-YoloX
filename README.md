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

Justify two codes in data_auguments.py and demo_track.py
====
📍 yolox/data/data_auguments.py

find preproc function to replace as the following.

        def preproc(img, input_size, swap=(2, 0, 1)):
            if len(img.shape) == 3:
                padded_img = np.ones((input_size[0], input_size[1], 3), dtype=np.uint8) * 114
            else:
                padded_img = np.ones(input_size, dtype=np.uint8) * 114

            r = min(input_size[0] / img.shape[0], input_size[1] / img.shape[1])
            resized_img = cv2.resize(
                img,
                (int(img.shape[1] * r), int(img.shape[0] * r)),
                interpolation=cv2.INTER_LINEAR,
            ).astype(np.uint8)
            padded_img[: int(img.shape[0] * r), : int(img.shape[1] * r)] = resized_img

            padded_img = padded_img.transpose(swap)
            padded_img = np.ascontiguousarray(padded_img, dtype=np.float32)
            return padded_img, r


![3](https://user-images.githubusercontent.com/46515944/182105506-e1f7c5ae-bef2-48e0-bd98-2d2da6a8b9d8.png)

📍 tools/demo_track.py

Delete "self.rgb_means, self.std"

![image](https://user-images.githubusercontent.com/46515944/182105661-f68195dc-3576-473f-8e8a-bdfd6d271f75.png)

Downloas pretrain file of YOLOX
====
🔗 https://github.com/Megvii-BaseDetection/YOLOX

You can choose any you prefer to download,then put it in root folder.

![image](https://user-images.githubusercontent.com/46515944/182106488-be93ca38-501d-489e-bbec-4af6065ba9c3.png)

![image](https://user-images.githubusercontent.com/46515944/182106717-e40f59f7-e8bc-48cc-95ba-3160a4059220.png)


Test
====
    python tools/demo_track.py video -f exps/default/yolox_x.py -c yolox_x.pth --fp16 --fuse --save_result

If you successed, it would be like 👇👇

https://user-images.githubusercontent.com/46515944/182106947-ea3cd418-240f-4424-926c-47648183321d.mp4

The output would be in "YOLOX_outputs/yolox_x/track_vis"
![image](https://user-images.githubusercontent.com/46515944/182107105-aa8eac04-9622-423b-910b-23230ce1f8c0.png)

Here is the ouput I tested.

![palace_demo](https://user-images.githubusercontent.com/46515944/182107364-0d5c2dc1-ffad-4764-85a4-80f6f06c736c.gif)


Reference
====
https://github.com/ifzhang/ByteTrack
https://colab.research.google.com/drive/1bDilg4cmXFa8HCKHbsZ_p16p0vrhLyu0?usp=sharing#scrollTo=kcuzq_MJ1EmK
https://blog.csdn.net/kuweicai/article/details/120873335
