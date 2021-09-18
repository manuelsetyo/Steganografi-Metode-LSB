sampul = imread("sampul.jpg");
pesan = imread("pesan.jpg");

figure(1), imshow(sampul);
title("Gambar Sampul");
figure(2), imshow(pesan);
title("Gambar Pesan");

sampul = double(sampul);
pesan = double(pesan);

% jumlah bit gambar pesan yang akan disematkan di gambar sampul
imbed = 4; % bit ==> 2, 4, 8

% menggeser gambar pesan lebih dari (8-imbed) bit ke kanan
pesanshift = bitshift(pesan,-(8-imbed));

% menampilkan gambar pesan hanya dengan menyematkan bit di layar
% harus beralih dari LSB ke MSB
pesantampil = uint8(pesanshift);
pesantampil = bitshift(pesantampil,8-imbed);

% mengosongkan bit yang disematkan dalam gambar sampul
sampulkosong = sampul;
for i=1:imbed
    sampulkosong = bitset(sampulkosong,i,0);
end

% menambahkan gambar pesan dan gambar sampul
sampulkosong1 = imresize(sampulkosong,[250,250]);
sampulkosong1 = double(sampulkosong1);
stegno = uint8(sampulkosong1+pesanshift);

figure(3), imshow(stegno);
title("Gambar Stegano");

imwrite(stegno,"stegano.jpg");