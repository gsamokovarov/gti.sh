#!/bin/bash

#     ,---------------.
#    /  /``````|``````\\
#   /  /_______|_______\\________
#  |]      GTI |'       |        |]
#  =  .:-:.    |________|  .:-:.  =
#   `   X   --------------   X   '
#     ':-:'                ':-:'

GIT_NAME=git
GTI_SPEED=50
TERM_WIDTH=$(tput cols)
SLEEP_DELAY=$(echo "scale=3; ($TERM_WIDTH + $GTI_SPEED) / 10000.0" | bc)

init_space() {
  echo -e "\n\n\n\n\n\n"
}

move_to_top() {
  echo -n -e "\033[7A"
}

line_at() {
  if [ $1 -gt 0 ]; then
    echo -e "\033[$1C${2:0:$(($TERM_WIDTH - $1))}"
  else
    echo "${2:0:$TERM_WIDTH}"
  fi
}

draw_car() {
  move_to_top
  line_at $1   "   ,---------------."
  line_at $1   "  /  /\`\`\`\`\`\`|\`\`\`\`\`\`\\\\"
  line_at $1   " /  /_______|_______\\\\________"
  line_at $1   "|]      GTI |'       |        |]"
  if [ $(expr $1 % 2) -eq 0 ]; then
    line_at $1 "=  .-:-.    |________|  .-:-.  ="
    line_at $1 " \`  -+-  --------------  -+-  '"
    line_at $1 "   '-:-'                '-:-'  "
  else
    line_at $1 "=  .:-:.    |________|  .:-:.  ="
    line_at $1 " \`   X   --------------   X   '"
    line_at $1 "   ':-:'                ':-:'  "
  fi
}

clear_car() {
  move_to_top
  line_at $1 "  "
  line_at $1 "  "
  line_at $1 "  "
  line_at $1 "  "
  line_at $1 "  "
  line_at $1 "  "
  line_at $1 "  "
}

init_space
for i in $(seq 0 $TERM_WIDTH); do
  draw_car $i
  sleep $SLEEP_DELAY
  clear_car $i
done
move_to_top
exec "${GIT:-$GIT_NAME}" $@
