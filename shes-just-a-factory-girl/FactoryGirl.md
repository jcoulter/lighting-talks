She's just a factory girl,
Living in an Active Record World

## Lazy Attributes
	
	#For instance, if we had an attribute called formula_name....
	
	formula_name 'Formula One'
	
	#But we want to use Faker to randomly generate it...
	
	formula_name Faker::Lorem.characters(10) 
	
	#However if we create two formulas they would have the same name...enter lazy attributes
	
	formula_name { Faker::Lorem.characters(10) }
	
## Dependent Attributes

	factory :user do
		first_name "John"
		last_name  "Doe"
		email { "#{first_name}.#{last_name}@example.com" }
	end

## Transient Attributes
	
	#Static and dynamic attributes can be ignored.
	
	#Provide the name of the attribute to ignore and a default value.
	
	transient do
      quality ''
      entity ''
    end
	
	#You can access ignored attributes in the factory body. 
	
	quality_id { Quality.find_by(quality) || Defaults::QUALITY_TYPE_ID }

	#The default value is only important if you are using the attribute in a dependent attribute
	
## Inheritance 

	# This can be done, by simply nesting a factory under another
	
	factory :user do
		first_name "John"
		last_name  "Doe"
	
		factory :validated_user
			email { "#{first_name}.#{last_name}@example.com" }
		end
	end

## Associations
	
	# TODO

## Traits

## Callbacks

	after(:build) 
	before(:create) 
	after(:create) 
	after(:stub) 