!SLIDE
# Functional Testing

!SLIDE
# Functional Testing
(for websites)

!SLIDE

    @@@ ruby
    test "should get index" do
      get "/index"
      assert_response 200
    end

!SLIDE

    @@@ ruby
    test "should get index" do
      get "/index"
      assert_response 200
      assert_select "h1", "OurCompany"
    end


!SLIDE

    @@@ ruby
    test "should post contact form" do
      post "/contact", :post => {
        :email => "john@doe.com",
        :message => "I really like your site"
      }
      
      assert_response 201
    end

!SLIDE

    @@@ ruby
    test "should validate email" do
      post "/contact", :post => {
        :email => "jo@hn@do@e.com",
        :message => "I really like your site"
      }

      assert_response 406
      assert_select ".error", "Invalid email"
    end
