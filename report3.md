# **Lab Report 3**

***

## Part 1: Bugs

The bug that I will be focusing on is in the `reverseInPlace` method in the file `ArrayExamples.java`. 
Failure-inducing input:
```
@Test 
	public void testReverseInPlace2() {
    int[] input1 = { 1, 2, 3, 4, 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 4, 3, 2, 1}, input1);
	}
```
Input that doesn't induce a failure:
```
@Test 
	public void testReverseInPlace1() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
Symptom:
![Image](image.png)
Before code (with bug):
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) { 
      arr[i] = arr[arr.length - i - 1]; 
    }
  }
```
After code (without bug) :
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i]; 
      arr[i] = arr[arr.length - i - 1]; 
      arr[arr.length-i-1] = temp; 
    }
  }
```
The reason why the before code does not work is because `arr[i]` is being overriden by the reverse value. This means that the value at `arr[i]` cannot be set to the proper reverse element, which is why the test fails. The after code works because it stores the current element in `arr` in a `temp` variable, so that it is not overwritten. Also, `i` should be `< arr.length/2` because if you continue, then you will get the same output because it reverses the values twice. 

## Part 2: Researching Commands: `less`

1. `less - E [input file]`

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -E 911report/chapter-1.txt
*opens the file*
"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
*rest of the file, outputs the next page after pressing space*
*quits automatically*
```

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -E biomed/1471-2091-3-22.txt
*opens the file*
        Background
        The ubiquitin/proteasome-dependent proteolysis system
        has been implicated in a wide variety of cellular
        regulatory mechanisms, including transcription, signal
        transduction, and cell cycle control (reviewed in [ 1 ] ).
        The system employs a cascade of enzymatic reactions that
        lead to the covalent attachment of a chain of multiple
        ubiquitins to substrate proteins [ 2 ] . In many cases,
        modification by ubiquityl moieties targets proteins to the
*rest of the file, outputs the next page after pressing space*
*quits automatically*
```
For both of these code blocks, you can traverse the file one page at a time, and when you get to the end, it automatically quits and puts you back into the terminal.
2. `less - f [input file]`

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -f 911report/chapter-1.txt
*opens the file*
"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
*rest of the file, outputs the next page after pressing space*
(END)
```

For this code block, the command works as regular since it is a regular file.

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -f 911report/
*opens directory*
...skipping...
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)
```

In this code block, `-f` is allowing us to run `less` on a directory, even though nothing gets outputted.

3. `less - F [input file]`

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -f 911report/chapter-1.txt
*opens the file*
"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
*rest of the file, outputs the next page after pressing space*
(END)
```

In this code block, `less` works regularly because the file is longer than a page.

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -F plos/pmed.0020191.txt 

  
    
      
        
        The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
        Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
        biohistorical research; instead, it points out that such investigations are currently
        taking place without guidelines—ethical, scientific, moral, or religious. The question
        remains: if such guidelines were to be established, what individuals, institutions,
        governments, medical examiners, family members, or intrepid biographers are to be given
        permission? Who is to decide what is “historically significant”? Not to mention the
        meta-question: who is to decide who is to decide? I apologize to the authors if my brief
        comments [2] implied that they took a position on this issue.
      
    
  

itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$
```

Here, `less -F` prints the entire file and then exits without opening up another window because the file is less than a page long.
4. `less - p pattern [input file]`

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -p Tuesday 911report/chapter-1.txt
*opens the file*
Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.

    For those heading to an airport, weather conditions could not have been better for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul Aziz al Omari, who arrived at the airport in Portland, Maine.
*rest of the file, outputs the next page after pressing space*
(END)
```

In this code block, `-p Tuesday` makes it so the file starts at where the first Tuesday appears, which removes `"WE HAVE SOME PLANES"` from being outputted.

```
itztm@LAPTOP-CVDGHEVR MINGW64 ~/docsearch/technical (main)
$ less -p meta-question plos/pmed.0020191.txt
*opens the file*
        meta-question: who is to decide who is to decide? I apologize to the authors if my brief
        comments [2] implied that they took a position on this issue.



~
~
~
~
~
~
~
~
~
~
(END)
```

In this code block, it only prints the last sentence of the file because that is the first time `meta-question` appears in the file. 
My source is https://eng.libretexts.org/Bookshelves/Computer_Science/Operating_Systems/Linux_-_The_Penguin_Marches_On_(McClanahan)/05%3A_File_and_Directory_Management/3.06%3A_Working_with_Files_and_Directories/3.06.02%3A_Working_with_Files_and_Directories_-_less-more_Command 
