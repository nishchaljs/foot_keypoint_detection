# foot_keypoint
Light weight Foot Keypoint detection pytorch model

Checkpoints can be downloaded from:
https://drive.google.com/drive/folders/1smi84-OtgWJrh-nWITDZWCmlNbMa-Cyr?usp=sharing

# For training:


1. Download pre-trained MobileNet v1 weights mobilenet_sgd_68.848.pth.tar from: https://github.com/marvis/pytorch-mobilenet (sgd option). If this doesn't work, download from GoogleDrive.
   
2. To train from MobileNet weights, run python train.py --train-images-folder <COCO_HOME>/train2017/ --prepared-train-labels prepared_train_annotation.pkl --val-labels val_subset.json --val-images-folder <COCO_HOME>/val2017/ --checkpoint-path <path_to>/mobilenet_sgd_68.848.pth.tar --from-mobilenet

3. Next, to train from checkpoint from previous step, run python train.py --train-images-folder <COCO_HOME>/train2017/ --prepared-train-labels prepared_train_annotation.pkl --val-labels val_subset.json --val-images-folder <COCO_HOME>/val2017/ --checkpoint-path <path_to>/checkpoint_iter_420000.pth --weights-only

 4. Finally, to train from checkpoint from previous step and 3 refinement stages in network, run python train.py --train-images-folder <COCO_HOME>/train2017/ --prepared-train-labels prepared_train_annotation.pkl --val-labels val_subset.json --val-images-folder <COCO_HOME>/val2017/ --checkpoint-path <path_to>/checkpoint_iter_280000.pth --weights-only --num-refinement-stages 3. We took checkpoint after 370000 iterations as the final one.
 

# Vaidation
Run python val.py --labels <COCO_HOME>/annotations/person_keypoints_val2017.json --images-folder <COCO_HOME>/val2017 --checkpoint-path <CHECKPOINT


# Python Demo
python demo.py --checkpoint-path <path_to>/checkpoint_iter_370000.pth --video 0
or
python demo.py --checkpoint-path <path_to>/checkpoint_iter_370000.pth --images <path of image>
   
# Sample Output
![alt text](data/demo.jpg)
