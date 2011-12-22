!SLIDE
# Unit Testing

!SLIDE

    @@@ ruby
    def first_name(name)
      name.split(" ").first
    end

!SLIDE small

    @@@ ruby
    def first_name(name)
      name.split(" ").first
    end

    test "first name" do
      assert_equal "John", first_name("John Doe")
    end

!SLIDE small

    @@@ ruby
    def first_name(name)
      name.split(" ").first
    end

    test "first name" do
      assert_equal "John", first_name("John Doe")
      assert_instance_of String, first_name("John Doe")
    end


!SLIDE small

    @@@ ruby
    def first_name(name)
      name.split(" ").first
    end
    
    test "return first name" do
      assert_equal "John", first_name("John Doe")
    end

    test "return a string" do
      assert_instance_of String, first_name("John Doe")
    end

!SLIDE small

    @@@ ruby
    def first_name(name)
      name.split(" ").first
    end

    test "return first name" do
      assert_equal "Jane", first_name("Jane Doe")
      assert_equal "John", first_name("John Doe")
      assert_equal "Nice", first_name("Mr. Nice Guy")
    end

    test "return a string" do
      assert_instance_of String, first_name("John Doe")
    end

!SLIDE small

    @@@ shell
    Failure:
    test: return first name [dir/file_test:123]:
    <"Nice"> expected but was <"Mr.">

!SLIDE small

    @@@ ruby
    test "strip Mr. from the name" do
      assert_equal "John", first_name("Mr. John Doe")
    end

!SLIDE small

    @@@ ruby
    def first_name(name)
      name.gsub! /^Mr\.\s/, ''
      name.split(" ").first
    end

!SLIDE small

    @@@ ruby
    test "strip Mr. from the name" do
      assert_equal "John", first_name("Mr. John Doe")
    end

    test "strip Mrs. from the name" do
      assert_equal "Jane", first_name("Mrs. Jane Doe")
    end

!SLIDE small

    @@@ ruby
    def first_name(name)
      name.gsub! /^Mr(s\.*)\s/, ''
      name.split(" ").first
    end

!SLIDE small

    @@@ ruby
    test "strip the honorific from the name" do
      assert_equal "John", first_name("Mr. John Doe")
      assert_equal "Jane", first_name("Mrs. Jane Doe")
    end
    
!SLIDE small

    @@@ ruby
    test "return first name" do
      assert_equal "John", first_name("John Doe")
    end

    test "strip the honorific from the name" do
      assert_equal "John", first_name("Mr. John Doe")
      assert_equal "Jane", first_name("Mrs. Jane Doe")
    end

    test "return a string" do
      assert_instance_of String, first_name("John Doe")
    end