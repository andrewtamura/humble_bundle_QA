##Answers:

1. *Why does Chrome complain when a non-secure image is embedded on a secure site?*
2. *What problems could arise because of this and how?*

When browsing a secure site (HTTPS), all the network traffic is encrypted and authenticated. The browser knows that any resource loaded via HTTPS comes from the correct source and that the information has not been tampered with. This security guarantee is how online banking and other sensitive actions can be performed through a web browser. However, web pages are complex and often require fetching multiple resources. Some resources like external javascript can change the content of your webpage. This means that an unsecured URL for a javascript file could be altered by a malicious third-party to load a nefarious javascript file that does bad things to your online banking webpage. For example, changing the buttons so that you transfer your money into different account when you really meant to pay your bills. 

Loading an unsecured image resource is not as dangerous as a javascript resource, so Chrome only displays a yellow warning instead of a red one. But there is still danger in loading this unsecured image. A malicious third-party could be snooping your network traffic and will be able to read the HTTP request headers from this unsecured image. This means that any information in the URL from the page you are loading is visible to a snooper. This can be especially dangerous if you are browsing a site that stores your password, user cookie, or any other information in the URL. e.g. http://www.myonlineback.com?account_num=123456&password=password

3. *How does a hash table work?*

A hash table is a data structure that stores a value with an associated key. It works by applying a mathematical function to the key so that the associated value can be stored and retrieved into a particular place in an array. For example, if I want to store a key-value pair (Chickens, 25), the hash function would transform the key "Chickens" into a unique value that maps directly to where the value 25 is stored. If the underlying structure were an array of 10 buckets, the key "Chickens" might be hashed into the array index 4. When we put the value into the index-4 bucket of the array, we can quickly retrieve it based on the key "Chickens". The hash function should be able to distribute keys uniformly over the size of the hash table. 

4. *How does the number of elements stored in a hash table affect various operations you can perform on it?*

The load factor of a hash table is the relationship between the number of items stored and the number of spaces available in the hash table. As load factor increases and the hash table fills up, performance for insertion, lookup, and deleting may suffer. This performance degradation is due to in creased hash collisions. A hash collision is when different keys hash to the same value. If this happens, then the values are stored under the same hash, but now the values are stored in a different data structure one level below the initial array. Performance for insertions, lookups, and deletions on keys have have hash collisions are negatively impacted. 

5. *What is a prototype in JavaScript?*

Every javascript object has a prototype property. This property is a list of key value pairs that the runtime searches through when looking up a key. When you create a link to a different object through the prototype property, the runtime will continue to search through the linked object's prototype as well! This search will continue through the "prototype chain" until it reaches a null value. 

6. *Can you give an example where a prototype is useful?*

We can use the prototype property to create classes that objects can inherit from. Instead of reimplementing a method in every object, we can implement it once in the parent class and have all necessary objects inherit the method by linking to the parent object in the child class prototype. 

            function Person(){}
            Person.prototype.speak = function(){
                return "Hello!"
            };
            
            function Man(){}
            Man.prototype = new Person();
            
            var andrew = new Man()
            andrew.speak()
            // andrew says, "Hello!"






