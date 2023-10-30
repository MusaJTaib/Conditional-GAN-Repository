# Fashion-MNIST Dataset Augmentation with Conditional GAN

This folder contains code for training a conditional GAN (CGAN) on the Fashion-MNIST dataset and use the trained generator
to increase the dataset size when training a classifier, as well as compare the accuracy results for some classifiers with different ratios
of real and synthetic data.

The experiment was setup in the following order:

1. Divide the dataset in smaller sized datasets using the `divide_data.ipynb` script, so that it remains static for the other experiments. The 
data is saved in the `data` folder. 

2. Train the GAN for each of the divided datasets, so that when augmenting them, we're only using the dataset's samples. This is done in the
`train_gan.ipynb` script. The trained generators are saved in the `gan_models` folder.

3. After the data is divided and the generators are trained and saved, we can use them to train classifiers in augmented datasets by using two other scripts:

    * `get_augmented_results.ipynb` is used to train classifiers in the different sized datasets while maintaining the increase ratio of the dataset size constant. The results are appended to the csv's `cnn_results.csv`, `simple_cnn_results.csv` and `dense_results.csv`.
    
    * `augment_results_same_sized.ipynb` is used to train classifiers with datasets of the same size (10,000), but using different amounts of synthetic data. It's results are appended in the `10000_fixed.csv`.

    * In both files there are 3 kinds of classifiers defined, one is a single dense layer, the second is a simple CNN, and the third is a more complex CNN. The scripts run for one classifier at the time and the others must be commented when running.

4. After obtaining the results, the script `plot_results.ipynb` contains code to read the output files, and save plot some graphs, comparing the accuracy with different augmentations and ratios of synthetic and real data.
