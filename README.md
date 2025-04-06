import json

json_file = "payment.json"
with open(json_file, "r") as file:
    users = json.load(file)["users"]

# Initialize counters for each value
count_1010 = 0
count_530 = 0
count_668 = 0
count_1148 = 0
count_1970 = 0  # Initialize counter for 1970
count_other = 0

# Initialize totals for each category
count_1010_total = 0
count_530_total = 0
count_668_total = 0
count_1148_total = 0
count_1970_total = 0  # Initialize total for 1970
count_other_total = 0

service = 40

# Loop through users and process fee data
for user in users:
    fee_input = user.get("fee", "")
    
    sum = int(fee_input)

    # Special case for adding 1970 + 20
    if sum == 1970:
        sum += 20 + service
        print(f"1970 found, new value: {sum}")
        count_1970 += 1  # Increment count for 1970
        count_1970_total += sum  # Add the modified sum (1970 + 20)

    elif sum == 1010:
        sum += 10 + service
        print(f"1010 found, new value: {sum}")
        count_1010 += 1  # Increment count for 1010
        count_1010_total += sum  # Add the modified sum (1010 + 10)
    elif sum == 530:
        sum += 5 + service
        print(f"530 found, new value: {sum}")
        count_530 += 1  # Increment count for 530
        count_530_total += sum  # Add the modified sum (530 + 5)
    elif sum == 668:
        sum += 7 + service
        print(f"668 found, new value: {sum}")
        count_668 += 1  # Increment count for 668
        count_668_total += sum  # Add the modified sum (668 + 7)
    elif sum == 1148:
        sum += 12 + service
        print(f"1148 found, new value: {sum}")
        count_1148 += 1  # Increment count for 1148
        count_1148_total += sum  # Add the modified sum (1148 + 12)
    else:
        print('Other value')
        count_other += 1  # Increment count for "other" values
        count_other_total += sum  # Add the sum of "other" values

# Calculate total sum for all categories
total_sum = count_1010_total + count_530_total + count_668_total + count_1148_total + count_1970_total + count_other_total

# After the loop, print out the counts, totals for each category, and the overall total sum
print(f"Count of 1010: {count_1010} x (1010 + fee 10 + service 40) = {count_1010_total}")
print(f"Count of 530: {count_530} x (530 + fee 5 + service 40) = {count_530_total}")
print(f"Count of 668: {count_668} x (668 + fee 7 + service 40) = {count_668_total}")
print(f"Count of 1148: {count_1148} x (1148 + fee 12 + service 40) = {count_1148_total}")
print(f"Count of 1970: {count_1970} x (1970 + fee 20 + service 40) = {count_1970_total}")
print(f"Count of other values: {count_other} x total = {count_other_total}")
print(f"Total sum of all categories = {total_sum}")
