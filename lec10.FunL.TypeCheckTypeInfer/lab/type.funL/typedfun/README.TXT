Compiling and loading the typed micro-ML evaluator (TypedFun/README.TXT)
------------------------------------------------------------------------

Archive typedfun.zip contains the file mentioned below, in directory
TypedFun/

use fsharpi under linux 

dotnet fsi

#load "typedfun.fs";;
eval ex1 [];;


A. Loading evaluator and type checker for the explicitly typed language

   fsi TypedFun.fs

   open TypedFun;; // open module

   // These typechecks should succeed:
   typeCheck (Prim("+", CstI 5, CstI 7));;
   typeCheck ex1;;

   // This typecheck should throw exception:
   typeCheck exErr1;;

   typeCheck (Prim("=", CstI 1, CstI 2));;

   #q;;
