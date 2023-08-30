Business Understanding:

We are provided with a dataset of used car sales with 426k cars or transactions or records. Our task is to analyze the data using the industry standard CRISP-DM processes and identify key drivers for the car prices. Make necessary recomendation to the dealership.

Data Understanding & Data Prepatation(cleaning and sanitizing):

<Input Data understanding image> 
![Input_data_level_of_inconsistancies_on_input](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/16e5d85b-8bb1-4d3d-89d7-811add14a031)

(1) Data Cleaning, dropping all rows with Nan/Zero values the size reduced from [426880 rows to 80170 rows] Dropping 82% of the data set would yield bad results. Hence Imputing values (with KNNImputer) that are missign/zero are essential. This was done to treat all zero and missing values in price and odometer.

(2) KNNImputer was also choosen to impute cylinders, size, condition, title_status & drive. KNNImputer also fixes missing values with feature mean.  All these columns were also encoded with JamesSteinEncoder for Categorical encoding.

(3) Dropped color, model, id and VIN from the dataset that does not add value to the price of the car.

(4) Combined region and state to region_state, dropped individual region and state fields.

Modeling:

Choosing the Features and the right Model

(1) Started with Ridge model, tried scalled and unscalled data. Scalled yielded better results. Permutation importance suggested reion_state and odometer to have the best impact on price and would be ideal to chooe to reduce model features. MSE for test data set was high.

(2)Tried LASSO model with polynomial (degree=3) MSE for test data set was not any better.

(3)Tried simple linear regression, estimated VIF(variance Inflaction Factor) Features were reasonably corelated to each other. Performing correlation heat map I reduced the feature set by two (dropped cylinders and year) Post dropping VIF now was looking bettter than before.

Scoring model with reduced features:

<correlation heatmep image>
<IVF with all features image>
<IVF removing cylinder and year feature image>
![VIF_to_reduce_model_complexity](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/e9c9e9cb-a82e-4657-b161-cd7304f344ae)
![VIF_to_reduce_model_complexity_reduced](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/966a827e-c1c9-499a-8e82-20ffca2c0563)

Tried scoring on Ridge, LASSO, and Linear regression.
LinearRegression performend better (poly degree=1), MSE on test dataset improved slightly as well.
Performed GridSearch on hyperparameters on this LinearRegression model and decided on model__fit_intercept: False & model__positive: True this improved the model performance a ittle better with improved MSE on test dataset as well.

<Modeling Image with results and decision factors>
![Modeling_evaluation_results](https://github.com/aaghouse/ML_UsedCarsPrice/assets/90729963/a15bdbfb-ba59-4397-9da9-76385b3750f2)
Summary:

Summary Input dataset for Analysis is missing critical large 80+% which contributes to a large extent negative model stability. Given the data set we can say region_state where used cars are sold and odomer reading are the most critical to get the best price for the car.
Best model to use to predict would be LinearRegression, polunomial degree=1, hyper parameters model__fit_intercept: False & model__positive: True. Which means there has to be a compensating factor in addition to the data provided to get the best price of the used car.
Next Steps Iterate throguh the model LinearRegression, go throguh grid search to identify better features combination. Then rerun the model to see if it would effectively improve the model score and MSE values.
Next steps as seen below to iterate over Sequential Feature Selector with 3 features is making the test MSE worst. We are getting better results with two features and simple Linear Regression.

Next Steps as a followup:

Starting MSE's selector_train_mse 225976476575947.16 selector_test_mse 110708549952295.33

Iteration 1 LinearRegression Recommendation: First Run:** n_features_to_select=3 Features from best selector: Index(['cylinders_labenc', 'size_labenc', 'condition_labenc'], dtype='object')

Iteration 2 LinearRegression Following Recomendation Features from best selector: Index(['cylinders_labenc', 'size_labenc', 'condition_labenc'], dtype='object') test_mse 110709248246897.78 test MSE is getting worst train_mse 225976928803183.84

Deployment Summary and recomendation to the car dealer: 

Data Science and Input data Input data is critical to data science, prediction models and stability of the prediction models. Other way of looking at it is garbege in garbege out. Quality data in will produce Quality prediction results and study.
Input data has a total of 426880 records. Some of the critical data such as price and odometer has zero values, (7.7% and 0.46%) respectively. This can be effectively treated and we did that to derive meaningful results.

Other critical fields have large number of null values such as size(71.76%), cylinders(41.62%), condition(40.78%), manufacturer(4.13%) and Drive(30.58%) With this many number of null values reasonable prediction becomes just below average and unstable. With that said we have tried our best to resonably predict and highlight what is important for the customers when they buy used cars.

Findings Region and state where the used cars are seems to dictate the price. Great insights if you are planing to build inventory and or deciding to sell to that specific region. Odometer reading seems to be one of the highest indicator of the price and what customers will look for to aquire a car. The model also predicts just these two alone are not enough we do need to read other constraints or variables. Deduction from the top model.
Other models that we researched considers cylinters, size and condition to be the top features that will decide the price of the used car
