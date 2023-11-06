

- Controllable generation lets you control the features of the generated outputs
- It does not need a labeled training dataset

![[Screenshot 2023-10-12 at 1.28.16 AM.png]]

![[Screenshot 2023-10-12 at 1.27.43 AM.png]]

![[Screenshot 2023-10-12 at 1.30.28 AM.png]]


## Z-Space and Controllable Generation
- The input vector is tweaked to get different features on the output
- To control output features, you need to find directions in the Z-space
- To modify your output, you move around in the Z-space
![[Screenshot 2023-10-12 at 1.36.01 AM.png]]
![[Screenshot 2023-10-12 at 1.36.43 AM.png]]


## Challenges with Controllable Generation

#### Feature Correlation
- When trying to control one feature, others that are correlated change
![[Screenshot 2023-10-12 at 1.39.04 AM.png]]

#### Z-Space Entanglement
- Z-space entanglement makes controllability difficult, if not impossible
- Entanglement happens when z does not have enough dimensions
![[Screenshot 2023-10-12 at 1.40.22 AM.png]]


## Classifier Gradients
- Classifiers can be used to find directions in the Z-space
- To find directions, the updates are done just to the noise vector
![[Screenshot 2023-10-12 at 1.44.51 AM.png]]


