# TODO

That lookup times for dictionaries are an $$O(1)$$ operation is a *strange and counter-intuitive* fact, and why this is true is well
beyond the scope of this text, but it should give you an idea of the power of
dictionaries and why they are used so often: Checking if a key is present in a
dictionary or retrieving the value stored with that key are both **constant
time** $$O(1)$$ operations, irrespective of the number of elements
stored in that dictionary.


*with 1 important
difference.* Using `in` on a list will search through the entire list, and so
this will actually take longer to complete as more elements are added to the
list, because it is actually an $$O(N)$$ operation. As stated in the
introduction, dictionaries are not just convenient to use, but also very
efficient. In fact, they are so efficient that searching in a dictionary in
practice almost always is is an $$O(1)$$ operation (in very improbable cases,
the big $O$ might be $O(N)$). This means the search will take approximately the
same time if the dictionary contains 1 or **1 million** elements!
