# LAB2 – Understanding Scripts

## 1. Script: `print_numbers.sh`

### Purpose
This script prints numbers from 1 to 5 in sequence.  

### Code Explanation (line by line)
```bash
#!/bin/bash
# This script prints numbers from 1 to 5

for i in {1..5}   # Loop from 1 through 5
do
  echo $i         # Print the current value of i
done
```

- `#!/bin/bash` → Shebang line to tell the system to use Bash.  
- `for i in {1..5}` → A loop that goes from 1 to 5.  
- `do … done` → Commands inside this block run for each iteration.  
- `echo $i` → Prints the current number.  

### Example Run
```bash
$ bash print_numbers.sh
1
2
3
4
5
```

---

## 2. Script: `array_loop.sh`

### Purpose
This script demonstrates looping through an array of strings.  

### Code Explanation (line by line)
```bash
#!/bin/bash
# This script loops through an array

arr=("apple" "banana" "cherry")   # Define an array with 3 items

for item in "${arr[@]}"          # Loop through each element in array
do
  echo $item                     # Print the current element
done
```

- `arr=( … )` → Creates an array with three elements.  
- `for item in "${arr[@]}"` → Loops through all elements of the array.  
- `echo $item` → Prints the current array element.  

### Example Run
```bash
$ bash array_loop.sh
apple
banana
cherry
```
