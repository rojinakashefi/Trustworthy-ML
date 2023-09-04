This Repository is about Adversarial and Robustness in Machine Learning. 

- [Slides created my me](https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/Adversarial_tutorial.ipynb)

- [Codes by me](https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/Adversarial_tutorial.ipynb)

- [Tutorial website](https://adversarial-ml-tutorial.org/)

- [Tutorial video](https://www.youtube.com/watch?v=TwP-gKBQyic&ab_channel=StevenVanVaerenbergh)

Presented on NeurlPS 2018 by J. Z. Kolter and A. Madry.

-------

1. **Basic Attack**:  by maximizing loss of correct class label. (FGSM method: gradient of loss function with respect to perturbation and clip it to the bounding area)
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/Basic-Attack.png" title="" alt="" width="444">

2. **Target Attack**: by maximizing loss of correct class label and minimizing loss of target class label.
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/Target-Attack.png" title="" alt="" width="433">

3. **Binary Classification using Linear models on MNIST**
   
   * Basic model after 10 epochs:
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/basic-linear.png" title="" alt="" width="307">
   
   error rate of 0.0004 means 1 wrong in **test set**.
   
   * Noise created for Linear models:
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/linear-noise.png" title="" alt="" width="151">
   
   Vertical line (like a 1) in black pixels, and a cirlce (like a 0) in in white. The intuition here is that moving in the black direction, we make the classifier think the image is more like a 1, while moving in the white direction, more like a 0.
   
   * Model error rate:
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/errorrate-linear.png" title="" alt="" width="288">
   
   From 0.0004 error rate to 82.8% error rate.
   
   <img title="" src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/ad-linear.png" alt="" width="262">
   
   * Training Robust Classifier:
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/robust-classifier.png" title="" alt="" width="311">
   
   * Adversarial Training Set:
   
   <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/robust-error.png" title="" alt="" width="318">
   
   No adversarial attack can lead to more then 2.5% error on the test set.
   
   * Non-adversarial Training Set:
     
     <img title="" src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/non-adv-error.png" alt="" width="290">
     
     We’re getting 0.3% error on the test set. This is good, but not as good as we were doing with standard training; we’re now making 8 mistakes on the test set, instead of the 1 that we were making before.
     
     **Trade off** between **clean accuracy** and **robust accuracy**, and doing better on the robust error leads to higher clean error.
   
   * Optimal perturbation for this robust model:
     
     <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/opt-pert.png" title="" alt="" width="191">

4. **Neural Networks**
   
   1. Solving inner maximization problem
      
      1. Lower bounding techniques:
         
         1. **FGSM** : which takes gradient of loss function with respect to perturbation 
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/FGSM_conv2d.png" title="" alt="" width="261">
            
            Constructing adversarial examples usign FGSM on Conv2D mode.
            
            Error rate FGSM:
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/FGSM_error_rate.png" title="" alt="" width="157">
         
         2. **Projected Gradient Descent**:
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/projected-gradient.png" title="" alt="" width="252">
         
         3. **Steepest Descent:**
            
            <img title="" src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/steepest-descent.png" alt="" width="260">
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/steepest-error.png" title="" alt="" width="131">
         
         4. **Randomization:**
            
            Error rate with randomization:
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/random-error.png" title="" alt="" width="119">
         
         5. **Targeted Attack**
            
            Target attack = 2 (The actual 2 is unchanged, because the loss function in this case is always exactly zero)
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/2-attack.png" title="" alt="" width="301">
            
            Target attack = 0 (we are maximizing is the class logit for the zero minus the class logit for the true class. But we don’t actually care what happens to the other classes, and in some cases, the best way to make the class 0 logit high is to make another class logit even higher.)
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/0-attack.png" title="" alt="" width="328">
         
         6. **Targeted Attack (minimizing all other classes)**
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/fixed-0.png" title="" alt="" width="325">
         
         7. **Non-ℓ∞ norms**
            
            <img src="https://github.com/rojinakashefi/Adversarial-Robustness/blob/main/images/other-norms.png" title="" alt="" width="333">
      
      2. Exactly solving
         
         1. Mixed integer formulation
         
         2. Finding upper bound and lower bound
         
         3. Final integer programming formulation
         
         4. Certifying robustness
      
      3. Upper bounding technique
         
         1. Convex relaxation
         
         2. Interval-propagation-based bounds

5. Solving outer minimization problem
   
   1. Adversarial training with adversarial examples
   
   2. Relaxation-based robust training
   
   3. Training using provable criteria
