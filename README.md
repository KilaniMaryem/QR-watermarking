## Watermarking Project Overview
This project is focused on embedding a message, specifically a Universally Unique Identifier (UUID), into an image through the process of watermarking. The watermark is encoded as a QR code, and the QR code is embedded into the host image by modifying the least significant bit (LSB) of certain pixels in the image. Here's an explanation of each step:

1. Message Encoding
In this project, the message that will be embedded into the image is a UUID (Universally Unique Identifier), which is a unique string that can be used to identify an object or transaction. This UUID is then encoded into a QR code. QR codes are chosen because they can store a sufficient amount of data in a compact and error-tolerant format. This encoding ensures that the embedded message can be recovered even if some parts of the image are altered or damaged.

2. Host Image
A host image is selected to carry the watermark. This is the image that will be modified to include the QR code without significantly affecting its visual appearance. The host image is a regular image that contains content.

3. Key Generation
To embed the watermark in a way that allows for accurate extraction later, a key is generated. This key consists of a series of pixel locations within the host image, and for each location, a specific color channel (Red, Green, or Blue) is selected. These positions will be used to store the bits of the QR code, ensuring that the message is hidden in random locations across the image. The key allows us to extract the watermark later with the same sequence of positions.

4. Watermark Embedding
The watermark embedding process modifies the host image by embedding the QR code bits into the least significant bit (LSB) of selected pixels in the image. The LSB is the smallest bit in a pixel's color channel, and modifying it has a minimal impact on the visual appearance of the image. This means that the image will look almost identical to the original image, making the watermark nearly imperceptible to the human eye. 

5. Watermark Extraction
At a later stage, when it's necessary to retrieve the watermark, the extraction process begins. The watermark is extracted by reading the LSBs of the selected pixels specified by the key. Since the bits were originally stored in the LSBs, the values in these locations will represent the bits of the QR code. After gathering these bits, they are reassembled into the QR code's bitstream. Once the QR code is reconstructed, it can be decoded to retrieve the original UUID message embedded in the image.

By using the key for extraction, it is possible to recover the exact watermark. If the image is altered, the extracted watermark may become corrupted or unreadable, but if the image is unchanged, the original UUID message can be perfectly retrieved.