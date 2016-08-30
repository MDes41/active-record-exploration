### find_or_create(attributes, &block)

#### Finds the first record with the given attributes or creates the record with the attributes if the record is not found

#### Example:

#### Say we have a table of singers with columns first_name, last_name, and genre

    Singer.find_or_create_by(first_name: 'Taylor', genre: Pop)
      # => #<Singer id: 1, first_name: Taylor, last_name: nil, genre: Pop>
    Singer.find_or_create_by(first_name: 'Elvis')
      # => #<Singer id: 2, first_name: Elvis, last_name: nil, genre: nil>

#### Will create a new singer if you do not validate the fields
    Singer.find_or_create_by(genre: Pop)
      # => #<Singer id: 1, first_name: Taylor, last_name: nil, genre: Pop>
    Singer.find_or_create_by(genre: Rock)
      # => #<Singer id: 3, first_name: nil, last_name: nil, genre: Rock>
#### You should have all your fields validated or it will create rows without all fields or run all the attributes in the argument to validate authenticity.