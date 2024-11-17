package main

import (
	"errors"
	"fmt"
	"sort"
	"strconv"
)

func isnum(sus string) bool {
	//fmt.Println(sus)
	if sus == "'0'" || sus == "'1'" || sus == "'2'" || sus == "'3'" || sus == "'4'" || sus == "'5'" || sus == "'6'" || sus == "'7'" || sus == "'8" || sus == "'9'" {
		return true
	} else {
		return false
	}
}

func plus(num1 float64, num2 float64) float64 {
	return float64(num1 + num2)
}
func minus(num1 float64, num2 float64) float64 {
	return float64(num1 - num2)
}
func multip(num1 float64, num2 float64) float64 {
	return float64(num1 * num2)
}
func divide(num1 float64, num2 float64) float64 {
	return float64(num1 / num2)
}

func Calc(expression string) (float64, error) {
	if expression == "" {
		return 0, errors.New("error lol")
	}
	a := []string{}
	ctr := 0
	type rating struct {
		name     string
		priority int
		step     int
	}
	type nums struct {
		name int
		step int
	}
	b := []rating{}
	c := []nums{}
	for i := 0; i < len(expression); i++ {
		if isnum(strconv.QuoteRune([]rune(expression)[i])) {
			a = append(a, strconv.QuoteRune([]rune(expression)[i]))
			aye := strconv.QuoteRune([]rune(expression)[i])
			e, _ := strconv.Atoi(string(aye[1]))
			aboba := nums{
				name: e,
				step: i,
			}
			c = append(c, aboba)
		} else if rune(expression[i]) == rune('(') {
			a = append(a, string(strconv.QuoteRune([]rune(expression)[i])))
			ctr += 1
		} else if rune(expression[i]) == rune(')') {
			a = append(a, string(strconv.QuoteRune([]rune(expression)[i])))
			ctr -= 1
			if ctr == 0 {
				// pairs += 1 // this is not gonna work TwT
			}
		} else if rune(expression[i]) == '+' || rune(expression[i]) == '-' || rune(expression[i]) == '*' || rune(expression[i]) == '/' {
			a = append(a, string(strconv.QuoteRune([]rune(expression)[i])))
		}
	}
	if ctr != 0 {
		return 0, errors.New("error lol")
	}
	open := 0
	prirs := []int{}
	for x := 0; x < len(a); x++ {
		if a[x] == "'('" {
			open += 1
		} else if a[x] == "')'" {
			open -= 1
		} else if a[x] == "'+'" || a[x] == "'-'" {
			hmm := rating{
				name:     string(a[x][1]),
				priority: open * 2,
				step:     x,
			}
			prirs = append(prirs, (open * 2))
			b = append(b, hmm)
		} else if a[x] == "'*'" || a[x] == "'/'" {
			hmm := rating{
				name:     string(a[x][1]),
				priority: 1 + (open * 2),
				step:     x,
			}
			prirs = append(prirs, (1 + open*2))
			b = append(b, hmm)
		}
	}
	var res float64
	sort.Ints(prirs)
	sort.Slice(prirs, func(i, j int) bool {
		return prirs[i] > prirs[j]
	})
	if len(b) >= len(c) {
		return 0, errors.New("error lol")
	}
	for x := 0; x < len(prirs); x++ {
		for y := 0; y < len(b); y++ {
			if prirs[x] == b[y].priority {
				if b[y].name == "+" {
					one := false
					two := false
					here := []int{}
					for f := 0; f < len(c); f++ {
						if (b[y].step + 1) == c[f].step {
							one = true
							here = append(here, c[f].name)
						} else if (b[y].step - 1) == c[f].step {
							two = true
							here = append(here, c[f].name)
						}
					}
					if one == true && two == true && res == 0 {
						res = plus(float64(here[0]), float64(here[1]))
					} else if res != 0 {
						res = plus(res, float64(here[0]))
					}
				} else if b[y].name == "-" {
					one := false
					two := false
					here := []int{}
					for f := 0; f < len(c); f++ {
						if (b[y].step + 1) == c[f].step {
							one = true
							here = append(here, c[f].name)
						} else if (b[y].step - 1) == c[f].step {
							two = true
							here = append(here, c[f].name)
						}
					}
					if one == true && two == true && res == 0 {
						res = minus(float64(here[0]), float64(here[1]))
					} else if res != 0 {
						res = minus(res, float64(here[0]))
					}
				} else if b[y].name == "*" {
					one := false
					two := false
					here := []int{}
					for f := 0; f < len(c); f++ {
						if (b[y].step + 1) == c[f].step {
							one = true
							here = append(here, c[f].name)
						} else if (b[y].step - 1) == c[f].step {
							two = true
							here = append(here, c[f].name)
						}
					}
					if one == true && two == true && res == 0 {
						res = multip(float64(here[0]), float64(here[1]))
					} else if res != 0 {
						res = multip(res, float64(here[0]))
					}
				} else if b[y].name == "/" {
					one := false
					two := false
					here := []int{}
					for f := 0; f < len(c); f++ {
						if (b[y].step + 1) == c[f].step {
							one = true
							here = append(here, c[f].name)
						} else if (b[y].step - 1) == c[f].step {
							two = true
							here = append(here, c[f].name)
						}
					}
					if one == true && two == true && res == 0 {
						res = divide(float64(here[0]), float64(here[1]))
					} else if res != 0 {
						res = divide(res, float64(here[0]))
					}
				}
			}
		}
	}
	return res, nil
}

func main() {
	fmt.Println(Calc(""))
}
