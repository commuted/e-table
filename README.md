# e-table and Mystery solved
E192, E96, E48 resistors IEC-60063-2015



E192, E96, E48 are precision 3, while E24, E12, E6, and E3 are precision 2. Read about the mystery.  

        '''python
        from math import floor, log10
        #decade e table
        def e_decade_table(es:int=96, precision:int=3,decade:int=1)->list:
            resistors = [10**(decade-1)]
            for i in range(1,es)  : # one decade
                value = (10**(i/es)) # value
                value = value * 10**(decade-1)
                sig_digit = round(value, -int(floor(log10(abs(value)))) + (precision - 1))        
                resistors.append(sig_digit)
            return resistors
        '''
The mystery is solved... E24, E12, E6 and E3 are not mathematically derived.

From IEC-60063-2015

"NOTE The values of the E24 series in the range of 27 through 47, and the value 82, divert from the exact mathematical rule. However, a correction of this deviation has never seemed appropriate in light of the historical relevance of this series, having been established prior to the 1952 release of the first edition of this standard."

        '''
        E24, E12, E6, E3
        10, 10, 10, 10
        11
        12, 12
        13
        15, 15, 15
        16
        18, 18
        20
        22, 22, 22, 22
        24
        27, 27
        30
        33, 33, 33
        36
        39, 39
        43
        47, 47, 47, 47
        51
        56, 56
        62
        68, 68, 68
        75
        82, 82
        91
        '''
        

