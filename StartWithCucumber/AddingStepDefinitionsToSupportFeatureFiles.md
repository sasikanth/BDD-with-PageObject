# Add step definitions to support feature files

Create "step_definitions" folder using:

`mkdir step_definitions`

![alt text](https://raw.githubusercontent.com/hy1984427/BDD-with-PageObject/master/images/CreateStepDefinitionsFolder.png "Create step_definitions folder")

Create "calculator_steps" to support calculator features:

`cd step_definitions`

`touch calculator_steps.rb`

![alt text](https://raw.githubusercontent.com/hy1984427/BDD-with-PageObject/master/images/CreateCalculatorStepsRB.png "Create calculator_steps.rb")

Edit "calculator_steps.rb" to contain following content:

<pre><code># encoding: utf-8
begin require 'rspec/expectations'; rescue LoadError; require 'spec/expectations'; end
require 'cucumber/formatter/unicode'
$:.unshift(File.dirname(__FILE__) + '/../../lib')
require 'calculator'

Before do
  @calc = Calculator.new
end

After do
end

Given /I have entered (\d+) into the calculator/ do |n|
  @calc.push n.to_i
end

When /I press (\w+)/ do |op|
  @result = @calc.send op
end

Then /the result should be (.*) on the screen/ do |result|
  @result.should == result.to_f
end
</pre></code>

![alt text](https://raw.githubusercontent.com/hy1984427/BDD-with-PageObject/master/images/CalculatorStepsRB.png "calculator_steps.rb content")
