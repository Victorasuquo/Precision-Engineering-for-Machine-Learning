# Precision-Engineering-for-Machine-Learning #
 ### < ABOUT  ME> 

    Victor Jacob Asuquo, Python/Machine Learning Instructor at Start Innovation Hub, Uyo - Nigeria 

    An Open source Contributor, passionate and inquisitive python Engineer who brings wealth of expertise in crafting cutting-edge solutions that transcend industries and drive business success. I am eager to learn and share the know I have about Python programming and communities.

    At the moment I am Working on an open source Library, a beginner friendly library that allows beginners to dive into the world of python Data Science and Machine Learning. The Library allows user to generate sales Dataset and do some manipulations with the  dataset and learn Data Science faster. Although the library is not yet published, It will be made public as soon as possible.

### < EDUCATION >
    Currently Pursuing a Bachelors Degree in Electrical/Electronics Engineering at University of Uyo, Nigeria

### < SESSION DETAILS >
     TOPIC: CodeLab: Precision Engineering for Machine Learning   

### < DESCRIPTION>
    As we all know about the World of AI Automating different Task and making it easier to the things perceived to be difficult. However, Machine Learning or Artificial Intelligence Generally is based on data. In some cases we observed Machine Learning Models being biased and performing poorly when used. How do you boost the performance and Accuracy of Machine Learning Models leveraging Log Loss, Gradient Descent, Cost Function, Vectorization, Feature Engineering, sigmoid function etc. Using the right Matrix for your model is critical.

    In this practical Codelab session we will dive into the basics of building Machine Learning
    Models with an increased performance using the techniques mentioned earlier using Jupyter notebook. 


### < CONCLUSION >
    I believe Given the oppurtunity we can leverage the oppurtuinity to do Great things.



{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Tce3stUlHN0L"
      },
      "source": [
        "##### Copyright 2024 Google LLC."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "cellView": "form",
        "id": "tuOe1ymfHZPu"
      },
      "outputs": [],
      "source": [
        "#@title Licensed under the Apache License, Version 2.0 (the \"License\");\n",
        "# you may not use this file except in compliance with the License.\n",
        "# You may obtain a copy of the License at\n",
        "#\n",
        "# https://www.apache.org/licenses/LICENSE-2.0\n",
        "#\n",
        "# Unless required by applicable law or agreed to in writing, software\n",
        "# distributed under the License is distributed on an \"AS IS\" BASIS,\n",
        "# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.\n",
        "# See the License for the specific language governing permissions and\n",
        "# limitations under the License."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "-QhPWE1lwZHH"
      },
      "source": [
        "# Gemini API Python quickstart"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "fa7c47ae6451"
      },
      "source": [
        "\n",
        "  \n",
        "  \n",
        "  \n",
        "\n",
        "    View on Google AI\n",
        "  \n",
        "    Run in Google Colab\n",
        "  \n",
        "    View source on GitHub\n",
        "  "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "db29b8d4247e"
      },
      "source": [
        "This tutorial shows you how to get started with the Gemini API using the Python SDK."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "NNNg43Ymw54e"
      },
      "source": [
        "## Prerequisites\n",
        "\n",
        "You can run this tutorial in Google Colab, which doesn't require additional environment configuration.\n",
        "\n",
        "Alternatively, to complete this quickstart locally, see the Python guidance in [Get started with the Gemini API](https://ai.google.dev/tutorials/quickstart)."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "kHkHARdb1ZID"
      },
      "source": [
        "## Install the SDK\n",
        "\n",
        "The Python SDK for the Gemini API is contained in the [`google-generativeai`](https://pypi.org/project/google-generativeai/) package. Install the dependency using pip:"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 2,
      "metadata": {
        "id": "J6Pd9SFJ1yVi"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "\u001b[?25l     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m0.0/137.4 kB\u001b[0m \u001b[31m?\u001b[0m eta \u001b[36m-:--:--\u001b[0m\r\u001b[2K     \u001b[91m━━\u001b[0m\u001b[91m╸\u001b[0m\u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m10.2/137.4 kB\u001b[0m \u001b[31m?\u001b[0m eta \u001b[36m-:--:--\u001b[0m\r\u001b[2K     \u001b[91m━━━━━━━━━━━\u001b[0m\u001b[91m╸\u001b[0m\u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m41.0/137.4 kB\u001b[0m \u001b[31m498.4 kB/s\u001b[0m eta \u001b[36m0:00:01\u001b[0m\r\u001b[2K     \u001b[91m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m\u001b[91m╸\u001b[0m\u001b[90m━\u001b[0m \u001b[32m133.1/137.4 kB\u001b[0m \u001b[31m1.3 MB/s\u001b[0m eta \u001b[36m0:00:01\u001b[0m\r\u001b[2K     \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m137.4/137.4 kB\u001b[0m \u001b[31m1.1 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\n",
            "\u001b[?25h"
          ]
        }
      ],
      "source": [
        "!pip install -q -U google-generativeai"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "EeMCtmx9ykyx"
      },
      "source": [
        "## Set up your API key\n",
        "\n",
        "To use the Gemini API, you'll need an API key. If you don't already have one, create a key in Google AI Studio.\n",
        "\n",
        "Get an API key\n",
        "\n",
        "In Colab, add the key to the secrets manager under the \"🔑\" in the left panel. Give it the name `GOOGLE_API_KEY`. Then pass the key to the SDK:"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 3,
      "metadata": {
        "id": "HTiaTu6O1LRC"
      },
      "outputs": [],
      "source": [
        "# Import the Python SDK\n",
        "import google.generativeai as genai\n",
        "# Used to securely store your API key\n",
        "from google.colab import userdata\n",
        "\n",
        "GOOGLE_API_KEY=userdata.get('GOOGLE_API_KEY')\n",
        "genai.configure(api_key=GOOGLE_API_KEY)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "CZPYk29o2No0"
      },
      "source": [
        "## Initialize the Generative Model\n",
        "\n",
        "Before you can make any API calls, you need to initialize the Generative Model."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 4,
      "metadata": {
        "id": "s-JqXcDe2hZ_"
      },
      "outputs": [],
      "source": [
        "model = genai.GenerativeModel('gemini-pro')"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "nXxypzJH4MUl"
      },
      "source": [
        "## Generate text"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 5,
      "metadata": {
        "id": "j51mcrLD4Y2W"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "In the bustling city of Evermore, there lived an ordinary schoolgirl named Anya. Little did she know that her life was about to take an extraordinary turn when she discovered a peculiar backpack.\n",
            "\n",
            "One morning, as Anya rummaged through her grandmother's attic, her eyes fell upon a dusty old backpack. Intrigued, she picked it up and unzipped it. Inside, she found a jumble of papers, trinkets, and a small, glowing crystal.\n",
            "\n",
            "As Anya reached out to touch the crystal, the backpack hummed with a soft energy. Suddenly, strange things began to happen. The zippers moved on their own, opening and closing compartments that revealed hidden pockets. Book pages turned themselves, revealing forgotten spells and incantations.\n",
            "\n",
            "Anya realized that this was no ordinary backpack. It was a magical backpack, imbued with ancient enchantments. Excited and overwhelmed, she carefully put on the backpack and felt its power surge through her.\n",
            "\n",
            "The next day at school, Anya couldn't resist testing out her new secret. She wished her homework was done, and to her amazement, the backpack performed its magic. The pen in her pocket began scribbling away, completing her assignments in a matter of minutes.\n",
            "\n",
            "As days turned into weeks, Anya's backpack became her most precious possession. She used its enchantments to help those in need, from repairing broken toys to granting small wishes. But she knew she had to be careful, lest the power of the backpack become too much for her to handle.\n",
            "\n",
            "One day, a nefarious sorcerer named Eldric learned of Anya's secret. Coveting its power, he plotted to steal the backpack. A fierce battle ensued, with Anya's backpack summoning magical creatures to her aid.\n",
            "\n",
            "In the end, Anya's courage and the power of the backpack prevailed. Eldric was defeated, and the city of Evermore was safe from his tyranny.\n",
            "\n",
            "From that day forward, Anya became known as the Guardian of the Magic Backpack. She used its enchantments wisely, always remembering the lesson she had learned: with great power comes great responsibility. And so, the legend of the magic backpack was passed down through generations, a testament to the power of kindness, courage, and the boundless imagination of a young schoolgirl.\n"
          ]
        }
      ],
      "source": [
        "response = model.generate_content(\"Write a story about a magic backpack.\")\n",
        "print(response.text)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "zUUAQS9u4biH"
      },
      "source": [
        "## What's next\n",
        "\n",
        "To learn more about working with the Gemini API, see the [Python tutorial](https://ai.google.dev/tutorials/python_quickstart).\n",
        "\n",
        "If you're new to generative AI models, you might want to look at the\n",
        "[concepts guide](https://ai.google.dev/docs/concepts) and the\n",
        "[Gemini API overview](https://ai.google.dev/docs/gemini_api_overview)."
      ]
    }
  ],
  "metadata": {
    "colab": {
      "name": "quickstart_colab.ipynb",
      "toc_visible": true
    },
    "kernelspec": {
      "display_name": "Python 3",
      "name": "python3"
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}
     


     