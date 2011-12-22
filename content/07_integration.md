!SLIDE
# Integration

!SLIDE
    @@@ ruby
    test "login and browse site" do
      get "/login"
      assert_response :success
      
      post_via_redirect "/login",
                        :username => "joe",
                        :password => "secret"
      
      assert_equal '/welcome', path
      assert_select "#username", "Welcome Joe!"
      
      get "/secret/stuff"
      assert_response :success
    end
