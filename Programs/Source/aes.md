```shell
echo 'USE_GF2N_LONG = 0' >> CONFIG.mine
make setup
make clean
make -j8 gen_input_f2n.x shamir-party.x malicious-shamir-party.x replicated-field-party.x malicious-rep-field-party.x

mkdir -p Player-Data/
echo 16 6b c1 be e2 2e 40 9f 96 e9 3d 7e 11 73 93 17 2a > gf2n_vals.in
./gen_input_f2n.x
mv gf2n_vals.out Player-Data/Private-Input-1

echo 16 2b 7e 15 16 28 ae d2 a6 ab f7 15 88 09 cf 4f 3c > gf2n_vals.in
./gen_input_f2n.x
mv gf2n_vals.out Player-Data/Private-Input-0

./Scripts/compile-run.py -E mascot aes
```
