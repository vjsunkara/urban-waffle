{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "f615f9c7",
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "from sklearn.ensemble import RandomForestClassifier\n",
    "from sklearn.model_selection import train_test_split\n",
    "from sklearn.metrics import accuracy_score\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "ec076867",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Load the data\n",
    "data = pd.read_csv(\"C:/Users/vijay/Desktop/creditcard.csv\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "60e115e8",
   "metadata": {},
   "outputs": [],
   "source": [
    "\n",
    "# Split the data into features and target\n",
    "X = data.drop(['Class'], axis=1)\n",
    "y = data['Class']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "id": "03e47634",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Split the data into training and test sets\n",
    "X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "id": "d17d0b06",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style>#sk-container-id-4 {color: black;background-color: white;}#sk-container-id-4 pre{padding: 0;}#sk-container-id-4 div.sk-toggleable {background-color: white;}#sk-container-id-4 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-4 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-4 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-4 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-4 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-4 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-4 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-4 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-4 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-4 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-4 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-4 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-4 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-4 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-4 div.sk-item {position: relative;z-index: 1;}#sk-container-id-4 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-4 div.sk-item::before, #sk-container-id-4 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-4 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-4 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-4 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-4 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-4 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-4 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-4 div.sk-label-container {text-align: center;}#sk-container-id-4 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-4 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-4\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>RandomForestClassifier(random_state=42)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-4\" type=\"checkbox\" checked><label for=\"sk-estimator-id-4\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomForestClassifier</label><div class=\"sk-toggleable__content\"><pre>RandomForestClassifier(random_state=42)</pre></div></div></div></div></div>"
      ],
      "text/plain": [
       "RandomForestClassifier(random_state=42)"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "\n",
    "# Train the model\n",
    "clf = RandomForestClassifier(random_state=42)\n",
    "clf.fit(X_train, y_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "id": "6677dbb9",
   "metadata": {},
   "outputs": [],
   "source": [
    "# Make predictions on the test set\n",
    "y_pred = clf.predict(X_test)\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "id": "20697802",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Accuracy: 99.96%\n"
     ]
    }
   ],
   "source": [
    "# Print the accuracy score\n",
    "acc = accuracy_score(y_test, y_pred)\n",
    "print(\"Accuracy: {:.2f}%\".format(acc * 100))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "id": "4f42592b",
   "metadata": {},
   "outputs": [],
   "source": [
    "from sklearn.model_selection import train_test_split\n",
    "from sklearn.linear_model import LogisticRegression\n",
    "from sklearn.metrics import confusion_matrix, classification_report\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "id": "d6e7c900",
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "d21fdde7",
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\vijay\\AppData\\Roaming\\Python\\Python38\\site-packages\\sklearn\\linear_model\\_logistic.py:458: ConvergenceWarning: lbfgs failed to converge (status=1):\n",
      "STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.\n",
      "\n",
      "Increase the number of iterations (max_iter) or scale the data as shown in:\n",
      "    https://scikit-learn.org/stable/modules/preprocessing.html\n",
      "Please also refer to the documentation for alternative solver options:\n",
      "    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression\n",
      "  n_iter_i = _check_optimize_result(\n"
     ]
    }
   ],
   "source": [
    "# train the model\n",
    "clf = LogisticRegression(random_state=0).fit(X_train, y_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "bf25f6c7",
   "metadata": {},
   "outputs": [],
   "source": [
    "# make predictions on the test set\n",
    "y_pred = clf.predict(X_test)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "7f72356f",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[[56829    35]\n",
      " [   43    55]]\n",
      "              precision    recall  f1-score   support\n",
      "\n",
      "           0       1.00      1.00      1.00     56864\n",
      "           1       0.61      0.56      0.59        98\n",
      "\n",
      "    accuracy                           1.00     56962\n",
      "   macro avg       0.81      0.78      0.79     56962\n",
      "weighted avg       1.00      1.00      1.00     56962\n",
      "\n"
     ]
    }
   ],
   "source": [
    "# evaluate the model\n",
    "print(confusion_matrix(y_test, y_pred))\n",
    "print(classification_report(y_test, y_pred))\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "dab57a78",
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "0a564f94",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.8"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
