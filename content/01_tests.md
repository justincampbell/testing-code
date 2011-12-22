!SLIDE
# Tests

!SLIDE

    @@@ ruby
    test "the truth" do
      assert true
    end

!SLIDE

    @@@ ruby
    test "the truth" do
      assert false
    end

!SLIDE

    @@@ ruby
    test "the truth" do
      assert false
    end
==
    @@@ shell
    Failure:
    test: the truth [dir/file_test:123]:
    <false> is not true.

