cp ./transaction-daily-couchbase/target/transaction-daily-couchbase-ocp.tar.gz ../deliver/final/
cp ./transaction-history-couchbase/target/transaction-history-couchbase-ocp.tar.gz ../deliver/final/
cp ./transaction-history/target/transaction-history-ocp.tar.gz ../deliver/final/
cp ./product-details-couchbase/target/product-details-couchbase-ocp.tar.gz ../deliver/final/
cp ./account-to-orcl/target/account-to-orcl-ocp.tar.gz ../deliver/final/
cp ./account-to-couchbase/target/account-to-couchbase-ocp.tar.gz ../deliver/final/
cp ./product-details-orcl/target/product-details-orcl-ocp.tar.gz ../deliver/final/
cp ./customer-couchbase/target/customer-couchbase-ocp.tar.gzv ../deliver/final/
cp ./customer-orcl/target/customer-orcl-ocp.tar.gz ../deliver/final/ 
cp ./cust-account-aggregation-couchbase/target/cust-account-aggregation-couchbase-ocp.tar.gz ../deliver/final/
cp ./transaction-daily-orcl/target/transaction-daily-orcl-ocp.tar.gz ../deliver/final/
cp ./account-aggregation/target/account-aggregation-ocp.tar.gz ../deliver/final/



wget https://github.com/alainpham/dl/raw/master/final/account-aggregation-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/account-to-couchbase-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/account-to-orcl-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/cust-account-aggregation-couchbase-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/customer-orcl-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/product-details-couchbase-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/product-details-orcl-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/transaction-daily-couchbase-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/transaction-daily-orcl-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/transaction-history-couchbase-ocp.tar.gz
wget https://github.com/alainpham/dl/raw/master/final/transaction-history-ocp.tar.gz

tar xzvf account-aggregation-ocp.tar.gz
tar xzvf account-to-couchbase-ocp.tar.gz
tar xzvf account-to-orcl-ocp.tar.gz
tar xzvf cust-account-aggregation-couchbase-ocp.tar.gz
tar xzvf customer-orcl-ocp.tar.gz
tar xzvf product-details-couchbase-ocp.tar.gz
tar xzvf product-details-orcl-ocp.tar.gz
tar xzvf transaction-daily-couchbase-ocp.tar.gz
tar xzvf transaction-daily-orcl-ocp.tar.gz
tar xzvf transaction-history-couchbase-ocp.tar.gz
tar xzvf transaction-history-ocp.tar.gz


projlist = account-aggregation account-to-couchbase account-to-orcl cust-account-aggregation-couchbase customer-couchbase customer-orcl product-details-couchbase product-details-orcl transaction-daily-couchbase transaction-daily-orcl transaction-history transaction-history-couchbase

for proj in $projlist
do
cd $proj
oc apply -f openshift.yml
oc start-build $proj --from-file=$proj.jar
cd ..
done

account-aggregation
account-to-couchbase
account-to-orcl
cust-account-aggregation-couchbase
customer-couchbase
customer-orcl
product-details-couchbase
product-details-orcl
transaction-daily-couchbase
transaction-daily-orcl
transaction-history
transaction-history-couchbase

