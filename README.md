# ML_UsedCarsPrice
What drives the price of a used car?
## OVERVIEW

In this application, you will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing. Your goal is to understand what factors make a car more or less expensive. As a result of your analysis, you should provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.

  ### Input Dateset: https://github.com/aaghouse/ML_UsedCarsPrice/blob/main/data.zip
  ### Google colab Notebook location: https://github.com/aaghouse/ML_UsedCarsPrice/blob/main/What_features_are_valuable_in_used_car.ipynb

<img width="374" alt="crisp" src="https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/2630ea14-df0c-430d-a03d-a832e1d72848">

![Input_data_level_of_inconsistancies_on_input](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/09123138-934c-424f-a029-c574f7a69931)

![Modeling_evaluation_results](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/1b6f9314-b008-4d7f-9413-6ddf194ffd16)

![Choosen_model_prediction_vs_test_data_sample_for_the_client](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/986c7d99-a601-45c1-9b55-ff891bfe8414)

## Summary
Input data is critical to data science, prediction models and stability of the models. Other way of looking at it is garbege in garbege out. Quality data in will produce Quality prediction results and valuable study.

Input data has a total of 426880 records. Some of the critical data such as price and odometer has zero values, (7.7% and 0.46%) respectively. This can be effectively treated and we did that to derive meaningful results.

Other critical fields have large number of null values such as size(71.76%), cylinders(41.62%), condition(40.78%), manufacturer(4.13%) and Drive(30.58%) With this many number of null values reasonable prediction becomes just below average and unstable. With that said we have tried our best to resonably predict and highlight what is important for the customers when they buy used cars.

Findings Region and state where the used cars are seems to dictate the price. Great insights if you are planing to build inventory and or deciding to sell to that specific region. Odometer reading seems to also be one of the highest indicator of the price and what customers will look for to aquire a car. The model predicts just these two alone are not enough we do need to read other constraints or variables. Deduction from the top model.

Other models that we researched considers cylinders, size and condition to be the top features that will decide the price of the used car.
### Analysis with summary https://github.com/aaghouse/ML_UsedCarsPrice/blob/main/Reportwithfindings.md
