# Deep-Learning
UW CSE599 Notes


Choosing Hyperparameters:
(without tons of GPUs)

Step 1: Check initial loss
Turn off weight decay, sanity check loss at initialization
e.g. log(C) for softmax with C classes

Step 2: Overfit a small sample 
Try to train to 100% training accuracy (~5-10 minibatches);
Loss not going down? LR too low, bad initialization
Loss explodes to Inf or NaN? LR too high, bad initialization

Step 3: Find LR that makes loss go down
Use the architecture from the previous step, use all training
data, turn on small weight decay, find a learning rate that
makes the loss drop significantly within ~100 iterations
Good learning rates to try: 1e-1, 1e-2, 1e-3, 1e-4

Step 4: Coarse grid, train for ~1-5 epochs
Choose a few values of learning rate and weight decay around
what worked from Step 3, train a few models for ~1-5 epochs.
Good weight decay to try: 1e-4, 1e-5, 0

Step 5: Refine grid, train longer
Pick best models from Step 4, train them for longer (~10-20
epochs) without learning rate decay

Step 6: Look at loss and accuracy curves
Step 7: GOTO step 5
