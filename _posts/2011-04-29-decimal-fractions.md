---
layout: post
title: 无限循环小数转化成分数（Java实现）
categories: [技术]
tags: [java, 算法]
---

如何精确的表达无限小数呢？这在计算机中是一个不可能完成的事情；但是无限循环小数是可以转化成分数，从而精确表达的；那问题来了，如何将无限循环小数转化成分数？例如0.（3），括号中是循环体，可以用1/3或3/9来表示。当然，我们想要的是分子分母不能再约分的最简分数。好吧：）来看看如何实现吧！

    import java.math.*;
     
    public class Decimal2Fraction {
        public String Repeating2Smallest(String repeating, String separate){
            String separate_l = separate.substring(0,1);
            String separate_r = separate.substring(1,2);
            String separate_p = ".";
            int index_p = repeating.indexOf(separate_p);
            int index_l = repeating.indexOf(separate_l);
            int index_r = repeating.indexOf(separate_r);
            BigInteger number = new BigInteger(repeating.substring(0,index_p));
            int n = index_l-index_p-1;
            BigInteger a = BigInteger.ZERO;
            if(n>0)a = new BigInteger(repeating.substring(index_p+1,index_l));
            int m = index_r-index_l-1;
            BigInteger b = BigInteger.ZERO;
            if(m<=0) return "请输入正确的循环体";
            if(m>0)b= new BigInteger(repeating.substring(index_l+1,index_r));
            BigInteger numerator = NumeratorFormula(n, m, a, b);
            BigInteger denominator = DenominatorFormula(n , m);
            BigInteger GCD = BigInteger.ZERO;
            while(!GCD.equals(BigInteger.ONE)){
                GCD = numerator.gcd(denominator);
                numerator = numerator.divide(GCD);
                denominator = denominator.divide(GCD);
            }
            return number+" "+numerator+"/"+denominator;
        }
        public BigInteger NumeratorFormula(int n,int m,BigInteger a,BigInteger b){
            return BigInteger.TEN.pow(m).subtract(BigInteger.ONE).multiply(a).add(b);
        }
        public BigInteger DenominatorFormula(int n,int m){
            return BigInteger.TEN.pow(m).subtract(BigInteger.ONE).multiply(BigInteger.TEN.pow(n));
        }
        public static void  Console(Object o){System.out.println(o.toString());}
        public static void main(String[] args) {
            Decimal2Fraction d2f = new Decimal2Fraction();
            String s = "0.2[22]";
            Console(d2f.Repeating2Smallest(s,"[]"));
        }
     
    }