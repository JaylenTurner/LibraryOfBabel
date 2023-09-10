### Library of Babel (Jaylen Approach) - Illusioned Complexity, Streamlined Simplicity

An overly simplified take on the library of babel algorithm. Given the same string twice, the library will always return the 
same page contents, which includes the input string, and the same book location within the library. This library contains 
every English string ever. Every story ever told or still yet to be told. Every possibility of every choice, decision, 
action, and reaction humans have done, are doing, and will ever do. Dive into the vast, never ending, infinite world of 
the Library of Babel.

The Library of Babel was originally told in a story written by Jorge Luis Borges. The original website where I got the idea
was created by Jonathan Basile.

Original website url: http://libraryofbabel.info/


```python
input_string = "Hello World."
```

```python
import random
import string
import hashlib

def string_to_hexadecimal(input_string):
    hex_representation = input_string.encode('utf-8').hex()
    return hex_representation

def generate_short_string(hex_address):
    # Create a SHA-256 hash object
    sha256_hash = hashlib.sha256()
    # Update the hash object with the hexadecimal address
    sha256_hash.update(hex_address.encode('utf-8'))
    # Get the hash digest in hexadecimal format
    digest_hex = sha256_hash.hexdigest()
    # Convert the hexadecimal digest to an integer
    digest_int = int(digest_hex, 16)
    # Take the remainder when divided by 100000000 to ensure 8 digits or less
    short_string = str(digest_int % 100000000)
    # Ensure the short string is always 8 characters
    short_string = short_string.rjust(8, '0')
    
    return short_string

def generate_page_content(hex_address, input_string):
    random.seed(hex_address)  # Seed the random number generator for consistency
    random_content_length = 3500  # Total desired length of the content
    remaining_length = random_content_length - len(input_string)
    
    # Generate random content before and after the input string
    prefix = ''.join(random.choice(string.ascii_lowercase) for _ in range(remaining_length // 2))
    suffix = ''.join(random.choice(string.ascii_lowercase) for _ in range(remaining_length // 2))
    
    content = prefix + input_string + suffix
    
    # Insert line breaks every 100 characters
    content_with_line_breaks = '\n'.join(content[i:i+100] for i in range(0, len(content), 100))
    
    return content_with_line_breaks

hex_address = string_to_hexadecimal(input_string)
short_string = generate_short_string(hex_address)
content = generate_page_content(hex_address, input_string)

# Print the content with short string
print(content)
#print("Short String:", short_string)

# Break up the short string
output_string = (
    f"\nBuilding: {short_string[0]}\n"
    f"Floor: {short_string[1:3]}\n"
    f"Book: {short_string[3:5]}\n"
    f"Page: {short_string[5:8]}"
)
print(output_string)
```

    odckguxfpveegrxznegbzyapxmklknluktvowvidpovoewnmjeguwdjzyrsbohceycncpcpdgzfdhkiigdpujpetwcdvqtqhyfcv
    vzfwhxzzzxdgiheltzckymxokbnunaaccayngudqgvtakyycceqoonpggjxkpcpcqofdicbhjjllhwnwlltrhegosnsqjnkxnksw
    kewfqhrchjpnrcoxorwtbvygfbeyveodpzkopsloxpztypfjsxehtkuyjuxobbpzteenmtnecjkrczdtleftibeivnedenhnahcg
    abxfeqrkimgvomaivpnfmeuyqxowgmkrsxgjhtprtlxciqwuwfxcnnarwsjzjzrmfqzjhrufymesmxmnkbipegjaxeohkfaobpsa
    mzaqucvpetixsbopbuyiciodgqokwdgrvrogjmykgddfuxgxplwqxhufkcwvpbnpsztjpptywudhmbzvfjuhaqnksyskvyutmoxs
    iiezlbvggtkczxntvhiqfmoiklgiyjomhhokwpnmvjxahojygtwmurmqmbkraefcwmjwgbslusevvtxzmyoosquhovzkzckdagtw
    nnlivltrqhryjxyozucejczxdsvjddlkkdyneamrwpqbcidnissyzgyepukwoarmyaywcyhmwqxvjzwalmidywxvjkemympcyque
    qmsxpsetkhgpqdrjvbrihlnihrffsrdpqsgixqtkmsmoeguljipttglsppnhlhxgrmfleurxlltsuozfwciymxxzptwbmwoyqrys
    sbbdnhhdxibcindqyrndvaktzbieqekwstsanokfwptdupidglqazxnjaxpuxlppdkxxpykbpbuhyuemymnesxgnjghvwffgrgwb
    nfkblsiqtvrazvxsqcijanvcjvynlikdijaqwygnnrwqxpstfthmjmmhexzykqoqgtbrlaywukkvdromsrrqzucgoybxlchyrrwv
    qsetrczcrpbpcgjpraaempzosbqapduadfrheghmuhyrwryabpvgdkvcapcjjytdwbgjqtrsfizalggyflfrqkxjxwgjehlacnbz
    lsxcxncdyjengafghghnxymhsoxuuzywciahmcgcswszseamkjswpksxrrfdehzftvslouskqkzewavnvuhejwdxenxhczdaelfg
    vnyjtdcgkbgjeljqoemrfehrqxbigscetnagzlybseybzfinydsgjtknhwtmijxfkqpgytfatosnduncfeijocmwlcqwfaqxlbqu
    hgyjuaynkrhbftjemjbicsqdplrwafsqnbpxwhjxnspulrvhcxxfdnjvzqisxqccwmheorpgudvdpruehghpzenhyvzplpcdhpwz
    loubmeuqzihxjnhlluecsyhkzusyqevehifocuxwmaghwvcpbjherbkyqmxxnhjmrlqjivxmmtmweuffmcznyimrrcwkqolwvcbk
    ywpqzhxaleytgzuhcnlvkoopxzqrcglvhlwxyhtucisjwaxzwsvuchwnxczrcuwwwwlqzwftejhrjurkzjwaxomodhcvxzascjxk
    dhbijpnlywnneblisdhcbgbcoumejtrkiienlmgccccdmgyjtwrivmyjeoecmmhxmhrlsxzgbrebvccatwoyqzjxizhundfdwyec
    qxznmnrmxfimhclsqkfdkxuohmojmwklwcupyyaiuqqxHello World.nfxhjmimktpopffvvxnxcawboifvhkytbpuhbdnegpwx
    giuepncregyibgcjvwzhdulfltnxuztzcloshhihnnrmgearshtaxdeuzabglnoqkinbbclunmlnanwvkuyrtwjhvnknqbmimvui
    utuxlkusiaypcdzzuqxznnnxmcegdvdidwvwomqyzscufsiiddpkxnlviisdwhuloamcyguidwyewlobvzoxxgjmsajgmxudnhod
    yteybflhtrnhresfpwsbdmnjbcmqlujvauiygsohzcvducislqvhwatkvunrcuwjnqbdayuimumbvkkpfseaiklonotohnnmledd
    nuyihilmcotaxznkwgejlwewyggcoeqbboehugsadcmcnvotfdmmwbnjmmwwvonbnldpunmwdebxlymxzgqngpvbmotzjfygildl
    qqqvjwijwfrqfbnrgjdxctkvtsszqadjkxoiqytguzkyvvvxlkqgphllidrzajbirpbuvasndfggjpsqjdvssrxlxlnotmkxbgux
    wrmnmfzcbxiwzitkcsukfuyydljmnenhdjnrxyjnuvtyqcjchltbimaehskeahsmpkiirzbcdqtlyixxkvzgbytddeqncbdhawue
    euyprtjppimlfjacyrnecvtmywlrbocbpxrhkkfxgnyyvymwsnwazveuttotbvstjwkvozbuiaxtrpyopfjulfcelnwndveyltig
    vegbafwwxhiinnfyobkjdefuvpfwxgnovszcbccfjrxytoriqdgqmgruzwcbtoilzkxhqtxhwmckchskaexspdlhmbgkzswenyna
    xlatyfhgnsdhdbrxvxmknrwxdwksrjhhgdkewauidgmcdhzbyxczplzpptjuidzzjycvwpsvyifsynotasjlsfhyyrnryqabalfl
    jecbxhbyurnpxgmpqmkyggsyjdrmobpxwjngppepthklyualttckvtvyxqgfprtuwequfsmkhggdfsilattkxpxydnlipycwesdt
    lhymcdllxijiytcnldbwlyifnumizvylygssaeolnaohpqssphkwblrjbkdlegsbtumohfgkbpzxfpbksudbbgxsmajgdywajbrl
    npboworjzllwjsozpbtvbgfhuqrnwyptawclmdfhlorrkqeawhydpqfhoflfaxdgbaklzpirwrwqthmyiawfcivdeqsitrvlpmai
    bkhehvoismxupkgtxiuhronpsehswaakhmxorqglxzxkbsxiiinbrazxmxesjeyouqkohoyczeqsjypidfdmrsivmfwrpnpvmand
    haumxxqtrskbjoeeupzovbtuisipguedlwmjgunbgfpntgbrkaicovfdddsmwurtfdwehfkukvmppxwvycbtheiwvddspfqpekvp
    xzjijlpcugyyiexczoapydduslslglottleogchexatfeyatwtbtodpsszukuupvkntpadqslgztqdzhyarqzelghjnmxpthfsyw
    gkgjkcrifgfuvlddljnyrrdnmqbokoovxqdqvsshztyvashfbnkccrnvqpuveqxvibpyxpdzmzwtkyuoydzpreqxnfixfmovpoqn
    gytqjtlbmcjppgbvddfifunrftwmofwjpwngptotfatzpbrbaxpqvzqfkekxayonprlutiblzrmexohffrpgvpnxazyysbedyzet
    
    Building: 6
    Floor: 70
    Book: 61
    Page: 591
