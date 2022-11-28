Datasets and DataFrames equals love. Although the processing functions of Datasets will cover most the cases needed to train a model, there are times when you’ll need to switch to a library like Pandas to access more powerful features or high-level APIs for visualisation. Fortunately, Datasets is designed to be interoperable with libraries like Pandas, as well as NumPy, PyTorch, TensorFlow, and JAX. In this video, we'll take a look at how we can quickly switch our data to Pandas DataFrames and back. As an example, let's suppose we're analysing Supreme Court cases from Switzerland. As usual we download our dataset from the Hub using the load_dataset() function, and you can see that the first element of the training set is an ordinary Python dictionary with various fields of interest. Now suppose that before we train any models, we'd like to explore the data a bit. For example we might be interested in knowing which legal area is most common or we might want to know how the languages are distributed across regions. Answering these questions with the native Arrow format isn't easy, but we can easily switch to Pandas to get our answers! The way this works is by using the set_format() method, which will change the output format of the dataset from Python dictionaries to Pandas DataFrames. As you can see in this example, each row in the dataset is represented as a DataFrame, so we can slice the whole dataset to get a single DataFrame of the dataset. The way this works under the hood is that the Datasets library changes the magic __getitem__() method of the dataset. The __getitem__() method is a special method for Python containers that allows you to specify how indexing works. In this case, the __getitem__() method of the raw dataset starts off by returning Python dictionaries and then after applying set_format() we change __getitem__() to return DataFrames instead. The Datasets library also provides a to_pandas() method if you want to do the format conversion and slicing of the dataset in one go. And once you have a DataFrame, you can find answers to all sorts of complex questions or make plots with your favourite visualisation library and so on. The only thing to remember is that once you are done with your Pandas analysis, you should reset the output format back to Arrow tables. If you don't, you can run into problems if you try to tokenize your text because it is no longer represented as strings in a dictionary. By resetting the output format, we get back Arrow tables and can tokenize without problem!