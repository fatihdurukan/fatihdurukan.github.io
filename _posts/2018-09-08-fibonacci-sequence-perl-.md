---
title: "File Based Database Management Software with Perl"
categories:
tags:
  - file
  - database
  - software
  - perl
header:
  teaser: /assets/images/What-is-Fibonacci-Sequence.jpg

---

<iframe src="https://drive.google.com/file/d/1zzxXsYmcuaHqD1xLUe78oxfHUrU0Lc6b/preview" width="100%" height="800em"></iframe>




 **Code is here!**{: .notice--danger}




 ```perl


use warnings;
use strict;
#Cwd for getting current directory
use Cwd;
my $dir = getcwd;
#we need to round numbers to find next fibonacci number.It isn't extra package,it comes with Perl.
use Math::Round;

#variables
my $command_line;
my $line;
my $curr;
my $phi;
my $next;
my $sonuc;
my $yedek;
my $values;
my $in;
my $pattern;
my $firstsearch;
my $ikinci;
my $index;
my $ozkan;


#golden ratio
$phi =1.6180339887;


$command_line=$ARGV[0];
#check the argument from command line if it's either empty or text file
if($command_line eq "\n" || $command_line eq '' ){
    print "\n";
    print "THERE IS NO ARGUMENT.PLEASE ENTER FILENAME:\n";

        $line = <STDIN>;

        if ($line =~ /\.txt\Z/) {
        $command_line = $line;
        print "\nFIBONACCI SEQUENCE IS BEING SEARCHED in $command_line \n";
        #merge current directory and filename in order to be opened
        $curr = $dir.'/'.$command_line;
        print "\nFULL DIRECTORY : $curr\n";
        #open the file for reading
        open ($in,$curr) or die "Can't open '$in': $!";;
        #assign values in file to $values
        $values = <$in>;
        close ($in);
        #for backup
        $yedek = $values;
        $ozkan = $values;
          #run program to find fibonacci sequence in values
        &program;

        } else {
        print "IT WASN'T A TEXT FILE. BYE BYE ! \n ";
        }
}else{
  #if filename comes from command line
  $curr = $dir.'/'.$command_line;
  #merge current directory and filename in order to be opened
  print "\nFULL DIRECTORY : $curr\n";
        if ($command_line =~ /\.txt/) {
            print "\nFIBONACCI SEQUENCE IS BEING SEARCHED in $command_line\n\n";
            #open the file for reading
            open  $in,  '<',  $curr;
            #assign string to $values
            $values = <$in>;
            close ($in);
            #for backup
            $yedek = $values;
            $ozkan = $values;
            #run program to find fibonacci sequence in values
            &program;
        } else {
            print "IT WASN'T A TEXT FILE. BYE BYE ! \n ";}
    }

#launch searching for fibonacci sequence
sub program {
#there are 2 arguments.First one is REGEX for digits from 1 digit through 6 digits.
#program will search starting from 1 digits numbers and will go on 2 digits,3 digits etc...
#second argument is for how many digits program will make group to search.
#if it is 3 program will make groups as 3 numbers like '234','853'.
#if it is 2 program will make groups as 2 numbers like '23','48' , '53' .
#second argument is for restriction. If sequence has less than 3 numbers, they will be ignored.
print "THESE FIBONACCI SEQUENCE NUMBERS ARE FOUND IN TEXT FILE : \n";
print &find_fib(0);
print &find_fib(1);
print &find_fib(2);
print &find_fib(3);
print &find_fib(4);
print &find_fib(5);


}

sub find_fib{
#this is main code for program

  $values = $ozkan;
  my $sayi = shift;
  $sonuc =0;

  #searching values with given REGEX
  while($values =~ /\d/g){
      #if_fibonacci subroutine checks whether number is fibonacci or not.

      $yedek=$';
      $firstsearch= $';
      #arranging number groups to be searched
      while ($firstsearch =~ /\d{$sayi}/g) {

        $ikinci=$&;
        $index = $';
        last;
      }
      my $arancak = $&.$ikinci;



#if number is fibonacci then it will continue for searching fibonacci sequence
      if(if_fibonacci($arancak) ==1){

          #adding first fibonacci number to $sonuc for printing
          $sonuc= $arancak;

          #calculate next fibonacci
          $next= next_fib($arancak);

          #$pattern should be rest of values not to repeat searching for same values

          $pattern = $index;
          #this while loop find  as many fibonacci sequence as it can in row
          while($pattern =~ /\A$next/g){
                $sonuc .= "-$&";
                $next= next_fib($&);
                $pattern = $';
          }

          #these if statements are  for just ignoring numbers that has less than 3 numbers
          #printing number that matches

          if($sayi == 0){
                if(length($sonuc) > 4){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
          elsif($sayi == 1){
                if(length($sonuc) > 6){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
          elsif($sayi == 2){
                if(length($sonuc) > 8){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
          elsif($sayi == 3){
                if(length($sonuc) > 10){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
          elsif($sayi == 4){
                if(length($sonuc) > 12){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
          elsif($sayi == 5){
              if(length($sonuc) > 14){
                  print "******************************************************\n";
                  print "$sonuc\n";
                }}
        #assign rest of values not to repeat searching for same values
        $values = $pattern;

  }
  }
  #use backup for start over for another digit search
  #print "deger $values\n";
  $values = $yedek ;
  #print "deger2 $yedek\n";


  "";
}

print "******************************************************\n\n";
print "Scripting Final Project / Fatih Durukan \n\n\n";

sub next_fib{
  my $n = shift;
  # we can find next fibonacci numbers multipling golden ratio.
  my $next = round ($n * $phi);
  $next;
}

#this subroutine is for checks if numbers perfect square
sub check_fib {
  my $n = shift;
  my $squared;
  $squared = int(sqrt($n));
  return 1 if($squared*$squared == $n);
}

#using perfect square, this subroutine will return 1 if number is fibonaccin number
sub if_fibonacci {
  my $n = shift;
  if($n==0){
    return 0;
  }else{
  return 1 if(check_fib(5*$n*$n + 4)==1 || check_fib(5*$n*$n - 4)==1);
}}


sub fibonacci {
    my $n = shift;

    return undef if $n < 0;

    my $fib;
    if ($n == 0) {
        $fib = 0;
    } elsif ($n == 1) {
        $fib = 1;
    } else {
        $fib = fibonacci($n-1) + fibonacci($n-2);
    }
    return $fib;
}

#Coded by Fatih Durukan
 ```
