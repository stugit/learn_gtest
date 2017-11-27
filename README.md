echo "# learn_gtest" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/stugit/learn_gtest.git
git push -u origin master
# compile gtest-all.o
g++ -isystem ${GTEST_DIR}/include -I${GTEST_DIR} -pthread -c ${GTEST_DIR}/src/gtest-all.c                                 c

# create a local lib file
ar -rv libgtest.a gtest-all.o

# Now compile your tests linking with the lib
g++ -isystem ${GTEST_DIR}/include -pthread tictactoe_tests.cpp libgtest.a -o my_tests

