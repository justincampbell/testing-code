!SLIDE
# Making it Pretty

!SLIDE
# Pretty Context

    @@@ ruby
    describe "object" do
      test "do something" do
        assert something
      end
      
      test "do something else" do
        assert something(else)
      end
    end
    
!SLIDE bullets incremental
# Pretty Context

* Describe object
* test == should
* "do this thing"

!SLIDE
# Pretty Context

    @@@ ruby
    context "object" do
      should "do something" do
        assert something
      end
      
      should "do something else" do
        assert something(else)
      end
    end

!SLIDE
# Pretty Syntax

    @@@ ruby
    # user_test.rb
    class UserTest < Test::Unit::TestCase
      context "age" do
        should "return a fixnum" do
          assert_instance_of Fixnum,
                             User.first.age
        end
      end
    end

!SLIDE
# Pretty Failures

    @@@ shell
    Failure:
    test: age should return a fixnum.
      (UserTest) [user_test.rb:4]
    Expected "age" to be an instance of
      Fixnum, not String.

!SLIDE
# Code Reuse

    @@@ ruby
    # user_test.rb
    class UserTest < Test::Unit::TestCase
      context "age" do
        setup do
          @user = User.first
        end
        
        should "return a fixnum" do
          assert_instance_of Fixnum, @user
        end
      end
    end

!SLIDE small

    @@@ ruby    
    context "first name" do
      setup do
        @john     = first_name "John Doe"
        @mr_john  = first_name "Mr. John Doe"
        @mrs_jane = first_name "Mrs. Jane Doe"
      end
      
      should "return the first name" do
        assert_equal "John", @john
      end

      should "strip the honorific from the name" do
        assert_equal "John", @mr_john
        assert_equal "Jane", @mrs_jane
      end

      should "return a string" do
        assert_instance_of String, @john
      end
    end
