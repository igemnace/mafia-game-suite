#!/usr/bin/env bash

tab=$'\t'

if [[ $1 == "-n" || $1 == "--nop" ]]; then
  echo "$2$tab$3" >> log
else
  echo "$1$tab$2" >> dead
  echo "kill$tab$1$tab$2" >> log
fi
