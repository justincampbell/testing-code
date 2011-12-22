!SLIDE
# Code Quality

!SLIDE
# Schlep
github.com/Movitas/schlep-ruby

!SLIDE

    @@@ ruby
    def event(type, message)
      envelope = {
        :timestamp => Time.now.to_f,
        :type =>      type,
        :message =>   message.to_json
      }.to_json
      
      @redis.rpush 'schlep', envelope
    end

!SLIDE
# Timestamp should be a Float

!SLIDE

    @@@ ruby
    context "timestamp" do
      should "be a float" do
        # ???
      end
    end

!SLIDE

    @@@ ruby
    def timestamp
      Time.now.to_f
    end

!SLIDE

    @@@ ruby
    def event(type, message)
      envelope = {
        :timestamp => timestamp,
        :type =>      type,
        :message =>   message.to_json
      }.to_json
    
      @redis.rpush 'schlep', envelope
    end

!SLIDE

    @@@ ruby
    context "timestamp" do
      should "be a float" do
        assert_instance_of Float,
                           Schlep.timestamp
      end
    end

!SLIDE
# Yay!

!SLIDE
# Envelope should be valid JSON

!SLIDE

    @@@ ruby
    context "???" do
      should "be valid json" do
        # ???
      end
    end
    
!SLIDE

    @@@ ruby
    context "envelope" do
      should "be valid json" do
        assert_nothing_raised(Exception) {
          JSON.parse(
            Schlep.envelope "test_type",
            { :one => { :two => 3 }}
          )
        }
      end
    end
    
!SLIDE

    @@@ ruby
    def envelope(type, message)
      {
        :timestamp => timestamp,
        :type =>      type,
        :message =>   message.to_json
      }.to_json
    end
    
!SLIDE

    @@@ ruby
    def event(type, message)
      @redis.rpush 'schlep',
                   envelope(type, message)
    end

!SLIDE
# Test-Driven Development!

!SLIDE
    @@@ ruby
    :message => message.to_json
    
!SLIDE
# Message should be left alone if it's already valid JSON

!SLIDE small

    @@@ ruby
    context "serialize message" do
      should "leave valid json alone" do
        assert_equal "{\"one\":{\"two\":3}}",
          Schlep.serialize_message("{\"one\":{\"two\":3}}")
      end
    end

!SLIDE

    @@@ ruby
    def serialize_message(message)
      return message if message.is_a? String
      message.to_json
    end
    
!SLIDE

    @@@ ruby
    def envelope(type, message)
      {
        :timestamp => timestamp,
        :type =>      type,
        :message =>   serialize_message(message)
      }.to_json
    end
    
!SLIDE small

    @@@ ruby
    context "serialize message" do
      should "leave valid json alone" do
        assert_equal "{\"one\":{\"two\":3}}",
          Schlep.serialize_message("{\"one\":{\"two\":3}}")
      end
      
      should "leave strings alone" do
        assert_equal "test string",
          Schlep.serialize_message("test string")
      end
    end

!SLIDE
# Before & After

!SLIDE small

    @@@ ruby
    def event(type, message)
      # Creates an envelope
      # Parses the message to JSON
      # Parses the envelope to JSON
      # Sends the event to Redis
    end

!SLIDE small

    @@@ ruby
    def envelope(type, message)
      # Creates an envelope and parses to JSON
    end
    
    def event(type, message)
      # Sends an event
    end
    
    def serialize_message(message)
      # Parses a message to valid JSON
    end
    
    def timestamp
      # Returns a timestamp in the format we want
    end
    