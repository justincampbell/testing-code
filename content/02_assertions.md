!SLIDE
# Assertions

http://guides.rubyonrails.org/testing.html#assertions-available

!SLIDE
    @@@ ruby
    assert( boolean, [msg] )

Ensures that the object/expression is true.
 
!SLIDE
    @@@ ruby
    assert_equal( obj1, obj2, [msg] )
Ensures that obj1 == obj2 is true.

    @@@ ruby
    assert_not_equal( obj1, obj2, [msg] )
Ensures that obj1 == obj2 is false.
 
!SLIDE
    @@@ ruby
    assert_same( obj1, obj2, [msg] )
Ensures that obj1.equal?(obj2) is true.
 
    @@@ ruby
    assert_not_same( obj1, obj2, [msg] )
Ensures that obj1.equal?(obj2) is false.
 
!SLIDE
    @@@ ruby
    assert_nil( obj, [msg] )
Ensures that obj.nil? is true.
 
    @@@ ruby
    assert_not_nil( obj, [msg] )
Ensures that obj.nil? is false.
 
!SLIDE
    @@@ ruby
    assert_match( regexp, string, [msg] )
Ensures that a string matches the regular expression.
 
    @@@ ruby
    assert_no_match( regexp, string, [msg] )
Ensures that a string doesn’t match the regular expression.
 
!SLIDE small
    @@@ ruby
    assert_in_delta( expecting, actual, delta, [msg] )
Ensures that the numbers expecting and actual are within delta of each other.
 
!SLIDE
    @@@ ruby
    assert_throws( symbol, [msg] ) {
      block
    }
Ensures that the given block throws the symbol.
 
!SLIDE
    @@@ ruby
    assert_raise( exception1, ... ) {
      block
    }
Ensures that the given block raises one of the given exceptions.
 
    @@@ ruby
    assert_nothing_raised( exception1, ... ) {
      block
    }
Ensures that the given block doesn’t raise one of the given exceptions.
 
!SLIDE
    @@@ ruby
    assert_instance_of( class, obj, [msg] )
Ensures that obj is of the class type.
 
    @@@ ruby
    assert_kind_of( class, obj, [msg] )
Ensures that obj is or descends from class.
 
!SLIDE  
    @@@ ruby
    assert_respond_to( obj, symbol, [msg] )
Ensures that obj has a method called symbol.
 
!SLIDE small
    @@@ ruby
    assert_operator( obj1, operator, obj2, [msg] )
Ensures that obj1.operator(obj2) is true.
 
!SLIDE
    @@@ ruby
    assert_send( array, [msg] )
Ensures that executing the method listed in array[1] on the object in array[0] with the parameters of array[2 and up] is true. This one is weird eh?
 
!SLIDE
    @@@ ruby
    flunk( [msg] )
Ensures failure. This is useful to explicitly mark a test that isn’t finished yet.
 