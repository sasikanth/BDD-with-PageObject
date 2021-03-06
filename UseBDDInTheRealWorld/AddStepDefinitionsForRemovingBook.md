# Add step definitions for removing book

Similarly, we are going to add "remove_book.rb" under "features/step_definations".

`cd step_definations`

`touch remove_book.rb`

![alt text](https://raw.githubusercontent.com/hy1984427/BDD-with-PageObject/master/images/CreateRemoveBookRB.png "Create remove_book.rb")

Then edit it to contain following content:

<pre><code># encoding: utf-8
When /^I remove the book from my shopping cart$/ do
	openShoppingCart
	removeTheFirstItem
end

Then /^I should not see the book in my shopping cart$/ do
	verifyItemRemovedFromShoppingCart
	verifyItemRemovedNotShownInShoppingCart
end

def openShoppingCart
    clickElementBy("id","nav-cart")
end

def removeTheFirstItem
	sleep (10) #it's better to wait for js or AJAX executed complete, but there is not a general way we can follow in industry
	clickElementBy("xpath","//span[@class=\"a-declarative\"]/input")
end

def verifyItemRemovedFromShoppingCart
	confirm=findElementBy("class", "a-size-base")
	confirm.text.include?("was removed from Shopping Cart")
end

def verifyItemRemovedNotShownInShoppingCart
	book=findElementBy("xpath", "//span[@class=\"a-size-medium a-text-bold\"]")
	book.text.should == "Subtotal (0 item): $0.00"
end
</pre></code>

![alt text](https://raw.githubusercontent.com/hy1984427/BDD-with-PageObject/master/images/EditRemoveBookRB.png "Edit remove_book.rb")
