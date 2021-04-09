check: testimg.ppm testout.ppm testimg.bmp testout.bmp testimg.jpg testout.jpg testimg.ppm testoutp.ppm testimgp.jpg testoutp.jpg testorig.jpg testoutt.jpg
	cmp testimg.ppm testout.ppm && echo 'test reussit'
	cmp testimg.bmp testout.bmp && echo 'test reussit'
	cmp testimg.jpg testout.jpg && echo 'test reussit'
	cmp testimg.ppm testoutp.ppm && echo 'test reussit'
	cmp testimgp.jpg testoutp.jpg && echo 'test reussit'
	cmp testorig.jpg testoutt.jpg && echo 'test reussit'

testout.ppm:
	../src/djpeg -dct int -ppm -outfile testout.ppm testorig.jpg

testout.bmp:
	../src/djpeg -dct int -bmp -colors 256 -outfile testout.bmp testorig.jpg

testout.jpg:
	../src/cjpeg -dct int -outfile testout.jpg testimg.ppm

testoutp.ppm:
	../src/djpeg -dct int -ppm -outfile testoutp.ppm testprog.jpg

testoutp.jpg:
	../src/cjpeg -dct int -progressive -opt -outfile testoutp.jpg testimg.ppm

testoutt.jpg:
	../src/jpegtran -outfile testoutt.jpg testprog.jpg

clean:
	rm -f testout.ppm testout.bmp testout.jpg testoutp.ppm testoutp.jpg testoutt.jpg

.PHONY: check clean
