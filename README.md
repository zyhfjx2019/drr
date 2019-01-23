# drr
code for the paper "Personalized Context-Aware Re-ranking for E-commerce Recommendation Systems"

# dataset  
## the toy data for training/validation/test
rec_train_set.sample.data         8000 lines

rec_validation_set.sample.data    1000 lines

rec_test_set.sample.data          1000 lines


# train
### 1. drr-base

python main.py --train true  --train_set rec_train_set.sample.txt --validation_set rec_validation_set.sample.txt  --model_type 0 --batch_size 128 --train_epochs 10  --train_steps_per_epoch 10  --validation_steps  15  --early_stop_patience  3  --lr_per_step 1000 --saved_model_name drr_model_0.h5

### 2. drr-personalized-v1

python main.py --train true  --train_set rec_train_set.sample.txt --validation_set rec_validation_set.sample.txt  --model_type 1 --batch_size 128 --train_epochs 10  --train_steps_per_epoch 10  --validation_steps  15  --early_stop_patience  3  --lr_per_step 1000 --saved_model_name drr_model_1.h5

### 3. drr-personalized-v2

python main.py --train true  --train_set rec_train_set.sample.txt  --validation_set rec_validation_set.sample.txt  --model_type 2 --batch_size 128 --train_epochs 10  --train_steps_per_epoch 10  --validation_steps  15  --early_stop_patience  3  --lr_per_step 1000 --d_feature 19 --saved_model_name drr_model_2.h5

# test

### 1. drr-base

python main.py --test_set rec_test_set.sample.txt  --batch_size 2 --model_type 0 --saved_model_name drr_model_0.h5

### 2. drr-peronalized-v1

python main.py --test_set rec_test_set.sample.txt  --batch_size 2 --model_type 1 --saved_model_name drr_model_1.h5

### 3. drr-personalized-v2

python main.py --test_set rec_test_set.sample.txt  --batch_size 2 --model_type 2 --saved_model_name drr_model_2.h5 --d_feature 19

# metric evaluation (including Precision/MAP)
python metric.py rec_test_set.sample.txt.predict.out


