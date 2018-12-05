#!/bin/bash
set -e

function usage {
	cat <<EOF
Usage: $0 [-h] filename

Creates a jekyll post file with filled headers

-h  | Show help
EOF
}

while getopts "h" o; do
	case "$o" in
		h)usage;;
		:)echo "Missing option argument for -$OPTARG";exit 1;;
	esac
done
shift $((OPTIND -1))
fname="${@: -1}"
if [ -z "$@" ]; then
echo "Filename missing"
echo "The program will now exit"
exit 1
fi
d=$(date +%Y-%m-%d)
t=$(date +%T)
tz=$(date +%z) 
fileName="$d-$fname.md"
echo $fileName
if [ -e $fileName ]; then
read -p  "File of this name exists. Do you wish to delete it? (y/n) " answer
case ${answer:0:1} in
	y|Y )
		rm $fileName;;
	* )
		exit 0;;
esac
fi
touch $fileName
echo "---" >> $fileName
echo "layout: post" >> $fileName
echo "title: $fname" >> $fileName
echo "date: $d $t $tz" >> $fileName
echo -e "---\n" >> $fileName

vim + +star $fileName 
