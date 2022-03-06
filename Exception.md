if (name == null || name.equals("")) {
            throw new IllegalArgumentException("name cannot be null or empty!");
        } 
        đối với ngoại lệ mà đối số truyền vào ko hợp lý vd: đối số vào là name nhưng người dùng nhập "" hoặc null thì ta throw