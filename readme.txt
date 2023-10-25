I have used repository (https://github.com/amitpanwarIndia/adapter-bert-assignment) for my work on this Assignment, this is a fork repository of main repo (https://github.com/google-research/adapter-bert).

Original Adapter Bert is supported by tensorflow version 1.15, however I had to upgrade and modify the code to latest tensorflow version using tf_upgrade_v2 script provided by tensorflow.

Original Algorithim:

1. First call
	I have to run following command to train the model:

	!python ./adapter-bert-assignment-upgraded/run_classifier.py \
	  --task_name=MRPC \
	  --do_train=true \
	  --do_eval=true \
	  --data_dir=/content/MRPC \
	  --vocab_file=/content/uncased_L_12_H_768_A_12/vocab.txt \
	  --bert_config_file=/content/uncased_L_12_H_768_A_12/bert_config.json \
	  --init_checkpoint=/content/uncased_L_12_H_768_A_12/bert_model.ckpt \
	  --max_seq_length=128 \
	  --train_batch_size=32 \
	  --learning_rate=3e-4 \
	  --num_train_epochs=5.0 \
	  --output_dir=/tmp/adapter_bert_mrpc/
  
2. Main method (run_classifier.py):
	This method calls main method in run_classifier.py file which has definition for processors for different type of dataset like MRPC, COLA etc.
	It defined all arguments passed into variables, and setup processor to be used. It tokenize the data points, setup configuration, calls model class to build and train model, evaluate it and then test it.
	
3. optimization.py:
	This class returns optimizer for the model based on inputs provided by users, and used in main method.
	
4. tokenization.py:
	This class is used to tokenize the data, as well as to convert data points with unicode, case matching and other conversions used in main method.
	
5. modeling.py:
	This class is main class for this functionality as it train Bert model with Adapters, it consists code for original Bert model as well as added functionality for Adapter Bert in method get_adapter, feedforward_adapter which adds parameter to Bert as a feedforward adapter layer with a bottleneck.
	
I have used MRPC for original training 

https://github.com/amitpanwarIndia/adapter-bert-assignment/blob/master/AML_Assignment_2.ipynb

https://colab.research.google.com/drive/1ViXbghkf5KGmTlwu0VrLf7VfnidW6Zrn#scrollTo=a5DozA7WB4Nl


2. Modified Algorithim:

In this I have added new support for WNLI task with new dataset as new processor to the run_classifier.py class file.

https://github.com/amitpanwarIndia/adapter-bert-assignment/blob/master/AML_Assignment_2_Modified.ipynb

https://colab.research.google.com/drive/1WHogr8RiL32LLtnSkYEI1BcUCSNx1Av_#forceEdit=true&sandboxMode=true&scrollTo=QKxFvDIv089f
