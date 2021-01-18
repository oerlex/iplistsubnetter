#!/usr/bin/python3
import sys
import re
import getopt

def main(argv):
    ipList= ['']

    try:
        print(argv)
        if len(argv)!= 2:
            print ('Usage: ipList2Subnets.py -i <ipList>')
            sys.exit(2)
        opts, args = getopt.getopt(argv,"i:",["ifile="])

        print(opts)
    except getopt.GetoptError:
        print ('test.py -i <ipList>')
        sys.exit(2)
    for opt, arg in opts:
        if opt in ("-i", "--ifile"):
            ipfile = arg
            with open(ipfile) as f:
                ipList = f.readlines()
                ipList = [x.strip() for x in ipList]

    networkList = ['']
    ipStr = ipList[0]

    previousSplitted = re.split('(.*)\.(.*)\.(.*)\.(.*)', ipStr)

    for ip in ipList:
        octetSplitted = re.split('(.*)\.(.*)\.(.*)\.(.*)', ip)
        #print(octetSplitted)
        octetSplitted[4]='0'
        if octetSplitted[1:-2]!=previousSplitted[1:-2]:
            #print(octetSplitted[1])
            ipNetwork = ('.'.join([str(elem) for elem in octetSplitted]))
            ipNetwork = ipNetwork[1:-3]
            networkList.append(ipNetwork)
        previousSplitted=octetSplitted


    with open('networklist.txt', 'w') as f:
        for item in networkList:
            print(item)
            f.write("%s\n" % item)


if __name__ == "__main__":
   main(sys.argv[1:])
