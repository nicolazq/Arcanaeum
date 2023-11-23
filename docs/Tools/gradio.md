
![gradio](https://www.gradio.app/_app/immutable/assets/gradio.8a5e8876.svg)

- <https://www.gradio.app/guides/quickstart>
- <https://www.gradio.app/guides/sharing-your-app>

- <https://scikit-learn.org/stable/auto_examples/linear_model/plot_iris_logistic.html>

```
from sklearn.linear_model import LogisticRegression
import numpy as np
import pickle

# Defining arrays for training
x_train = np.array([[0.5, 1.5], [1, 1], [1.5, 0.5], [1, 0.5], [2, 0], [2, 0.5], [1, 2], [2, 2], [0.5, 3], [2, 1.5], [1, 2.5], [3, 1]])
y_train = np.array([0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1])

# Training model
model = LogisticRegression()
model.fit(x_train, y_train)

# Saving the model
pickle.dump(model, open('trained_model_logreg.pkl', 'wb'))
```

```
from sklearn.linear_model import LogisticRegression
import gradio as gr
import pandas as pd
import numpy as np
import pickle

# Loading the model
model_loaded = pickle.load(open('trained_model_logreg.pkl', 'rb'))

# Defining a function for prediction
def predict(x1,x2):
    
    # Converting input values to np.ndarray
    x_array = np.array([float(x1),float(x2)])
    
    # Predicting
    prediction = model_loaded.predict([x_array])
    
    if prediction:
        return "POSITIVE ANSWER"
    else:
        return "NEGATIVE ANSWER"
    return

# Launching
demo = gr.Interface(
    fn=predict,
    inputs=["text", "text"],
    outputs="text",
    title='Simple Logistic Regression'
)

demo.launch()
```
