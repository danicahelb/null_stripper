# null_stripper
uses python to reformat raw data file

 ```python
 
import csv
import os

files = os.listdir('.')


for f in files:
	with open(f, 'rb') as csv_file:
		data = csv_file.read()
		with open("nul_stripped_" + f, 'w') as dest_file:
			dest_file.write(data.replace('\x00', ''))
			
	with open("nul_stripped_" + f, 'rb') as csv_file:
		r = csv.reader(csv_file, dialect='excel-tab')
		r.next()
		with open("new_" + f, 'w') as dest_file:
			w = csv.writer(dest_file)
			for line in r:
				w.writerow(line)
		# for i, c in enumerate(data):
		# 	if c== '\x00':
		# 		print i, repr(data[i-30:i]) + " *NUL " + repr(data[i + 1:i + 31])
 ```
