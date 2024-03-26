Encode = function(password)
    caesar = function(pass, type)
        nr = pass.len%10
        crypt = function(char, nr, type)
            if type == "enc" then return char+nr
            if type == "dec" then return char-nr
        end function    
        out = []
        for i in range(0, pass.len-1)
            c = pass[i].code    
            if c >= 48 and c <= 57 then 
                c = crypt(c, nr, type)
                if c < 48 then c = c+10
                if c > 57 then c = c-10    
            else if c >= 65 and c <= 90 then 
                c = crypt(c, nr, type)
                if c < 65 then c = c+26
                if c > 90 then c = c-26
            else if c >= 97 and c <= 122 then 
                c = crypt(c, nr, type)
                if c < 97 then c = c+26
                if c > 122 then c = c-26
            end if        
            out.push(char(c))
        end for
        return out.join("")
    end function
    output = caesar(password, "enc")
    return output
end function