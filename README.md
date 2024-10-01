ml-docker-app-demo

<h1>Machine Learning Docker Flask App</h1>

This project creates a simple machine learning model using the Iris dataset and serves it through a Flask API inside a Docker container. The app allows users to send data to an endpoint and get predictions from the model.

<h3>Overview</h3>
The project uses a DecisionTreeClassifier to classify iris flowers into three species: Setosa, Versicolor, and Virginica. The model is exposed as a REST API using Flask, and the entire application is packaged into a Docker container for easy deployment.

<h3>Instructions to Build and Run the Docker Container</h3>
1. Clone the Repository

`git clone https://github.com/yourusername/your-repository.gitcd your-repository`

2. Build the Docker Image
   
`sudo docker build -t ml-app .`

This will create a Docker image with the Flask app and the machine learning model.


3. Run the Docker Container
   Once the image is built, run the container, exposing the Flask app on port   4000 of your machine:

   `sudo docker run -p 4000:80 ml-app`

   
The Flask app will now be running, and you can access it via the external IP of your virtual machine or localhost if running locally.

<h3>Instructions to Test the ML Endpoint</h3>
You can test the endpoint using curl or any other tool (like Postman). 

`curl -X POST http://<vm-external-ip>:4000/predict -H "Content-Type: application/json" -d '{"input": [5.1, 3.5, 1.4, 0.2]}'` 

The input array corresponds to the features of an iris flower:
- Sepal length
- Sepal width
- Petal length
- Petal width

The API will return a JSON object with the predicted class label:

- `0`: Setosa
- `1`: Versicolor
- `2`: Virginica

  Example Output:
  `{
     "prediction: 0
   }
  `
  This indicates that the input flower was classified as a Setosa.

<h3>Additional Information</h3>

<h3>Troubleshooting</h3>
Firewall Configuration: Ensure that port 4000 (or the port you're using) is open in the firewall settings of your virtual machine.

<h3>Retraining the Model</h3>
To retrain the model, modify the train_model.py file and run it in your local environment or inside the Docker container:

`python3 train_model.py`

This will update the model and regenerate the `model.pkl` file.

