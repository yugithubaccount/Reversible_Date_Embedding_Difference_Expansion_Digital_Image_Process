Reversible Date Embedding
====================================================================

Embed Data Into a Picture reversibly using difference expansion

## Background

Reversible data embedding, which is also called lossless data embedding, embeds invisible data (which is called a payload or a watermark) into a digital image called *cover image* in a reversible fashion.

## Math principles

Since github is not good at handling math formulas, I did not write down all the formulas here, if you can read Chinese, you could see through <a href="README.pdf">README.pdf</a>, it is generated by Latex and all the formulas are included in it.

Otherwise you could see through the two papers listed in the References, they were written in English and all the principles are the same. However, there is a minor mistake in the second paper, 
          
The pixels in the picture are divided into four groups, M, N (Ne & Ne_), U by the threshold T.

It should be:

-   if |h| ≤ (T−1)/2 then M
-   if 2T +1 ≥|h|>(T−1)/2 then N
  -   if T ≥ |h| > (T−1)/2 then Ne
  -   if 2T + 1 ≥ |h| > T then Ne_ 
-   if |h|>2T +1 Then U

But the paper mistake (T-1)/2 for T/2.

## Step by step

**Step 1** Apply the integer difference expansion transform, also called the "integer" Haar wavelet transform, using the scaling function coefficients 1/2, 1/2 and the wavelet function coefficients 1, -1 to the Lena image horizontally to produce the two transformed 512 x 256 sub - images: one with horizontal average and one with horizontal detail. Likewise, you can apply the above operation vertically to produce the
two different 256 x 512 sub-images.

**Step 2** Print the name in English or Chinese on a paper and take a digital
picture of it, and then threshold it as an N*M binary image.

**Step 3** Concatenate the N rows of the binary image into an N*M bits as the
data to be embedded.

**Step 4** Apply the reversible data embedding method presented in the class
to the host 512x512 8-bit Lena image to produce a watermarked image
containing your signature.

**Step 5** Compute the difference image between the original and watermarked
versions of the Lena image. Show the histogram of the diffidence image. 

**Step 6** Extract the embedded binary printed signature and also restore the
original Lena image from the watermarked image obtained above.

## Demo Results

Originally Picture:

<img src="./figure/myname.JPG" alt="Orginally Picture">

Decoded Results:

<img src="./figure/d_watermark.jpg" alt="Decoded Results">

The original picture is 0-255 digit per pixel while the embedded data can only be 0-1, so their must be some data to lose. If the original data only contains 0-1, nothing will be lost.

## References

1. Jun Tian, Reversible Data Embedding Using a Difference Expansion, IEEE, 2003
3. Hyoung Joong Kim, Yun Qing Shi, Jeho Nam, Hyon-Gon Choo, Vasiliy Sachnev, A Novel Difference Expansion Transform for Reversible Data Embedding, IEEE, 2008
2. wikipedia.http://en.wikipedia.org/wiki/Haar_wavelet

---------------------------
2013@NCTU

By Wildflame(David Lin)

