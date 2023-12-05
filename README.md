LAB 4: You must do the project individually. In this HW you will design a backdoor detector for BadNets trained on the YouTube Face dataset using the pruning defense discussed in class. Your detector will take as input:

B, a backdoored neural network classifier with N classes.
Dvalid, a validation dataset of clean, labelled images.
What you must output is G a “repaired” BadNet. G has N+1 classes, and given unseen test input, it must:

Output the correct class if the test input is clean. The correct class will be in [1,N].
Output class N+1 if the input is backdoored. You will design G using the pruning defense that we discussed in class. That is, you will prune the last pooling layer of BadNet B (the layer just before the FC layers) by removing one channel at a time from that layer. Channels should be removed in decreasing order of average activation values over the entire validation set. Every time you prune a channel, you will measure the new validation accuracy of the new pruned badnet. You will stop pruning once the validation accuracy drops atleast X% below the original accuracy. This will be your new network B'. Now, your goodnet G works as follows. For each test input, you will run it through both B and B'. If the classification outputs are the same, i.e., class i, you will output class i. If they differ you will output N+1. Evaluat this defense on:
A BadNet, B1, (“sunglasses backdoor”) on YouTube Face for which we have already told you what the backdoor looks like. That is, we give you the validation data, and also test data with examples of clean and backdoored inputs.

To run the code: Go to the sv2448_Backdoor_attacks.ipynb and run all the cells sequentially. You can access all the bad net models, data as well as the repaired net models in the following below Drive link: https://drive.google.com/drive/folders/1M0ZXsYwuzXoOtsdeS4xuQF8x0QMNo405?usp=sharing

We conducted experiments using the pruned versions of neural networks obtained from the 2020 hacks git repository on clean datasets. Pruning was employed to eliminate affected layers in the bad networks, thereby altering their behavior for specific output classes. This technique is crucial in deep learning as it reduces both time and space complexity by decreasing the number of parameters, particularly towards the final layers of the neural network.

In our analysis, we observed varying test accuracies for the pruned bad networks on clean datasets. Specifically, we plotted the accuracy against the attack success rate for the validation dataset. Notably, the attack success rate was 6.954% when the accuracy dropped by at least 30%.

Subsequently, we endeavored to repair the bad networks by pruning them at different rates (2%, 4%, and 10%). The results for the repaired networks on clean test data and their corresponding attack success rates are as follows:

Combined 2% Drops Model:

Classification Accuracy: 95.90%
Attack Success Rate: 100.0%
Combined 4% Drops Model:

Classification Accuracy: 94.77%
Attack Success Rate: 99.98%
Combined 10% Drops Model:

Classification Accuracy: 84.54%
Attack Success Rate: 77.21%
These findings demonstrate the impact of pruning in enhancing the performance of the repaired networks, as reflected in both classification accuracy on clean test data and resilience against adversarial attacks.

