package coverage

import (
	"os"
	"testing"
	"time"
	//"fmt"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
const ErrD = "Expected: %d, got %d"
const ErrT = "Expected: %t, got %t"
const ErrS = "Expected: %s, got %s"

func TestLenOk(t *testing.T){
	var p People
	var expect int = 0
	n := p.Len()
	if n!= expect{
		t.Errorf(ErrD, expect, n)
	}
}

func TestLessOk(t *testing.T){
	var p People
	var expect bool = true
	p1 := Person{firstName: "Ivan", lastName: "Ivanov", birthDay: time.Date(1990,time.June, 8, 8,2,5,0,time.Local)}
	p2 := Person{firstName: "Ivan", lastName: "Petrov", birthDay: time.Date(1990,time.June, 8, 8,2,5,0,time.Local)}
	p3 := Person{firstName: "Petr", lastName: "Petrov", birthDay: time.Date(1990,time.June, 8, 8,2,5,0,time.Local)}
	p4 := Person{firstName: "Alex", lastName: "Sokolov", birthDay: time.Date(1985,time.June, 8, 8,2,5,0,time.Local)}
	p = append(p,p1)
	p = append(p,p2)
	p = append(p,p3)
	p = append(p,p4)
	for i := 0; i < len(p)-1; i++ {
		n := p.Less(i, i+1)
		if n != expect {
			t.Errorf(ErrT, expect, n)
		}
	}
}

func TestSwapOk(t *testing.T){
	var p People
	var expect People
	p1 := Person{firstName: "Ivan", lastName: "Ivanov", birthDay: time.Date(1990,time.June, 8, 8,2,5,0,time.Local)}
	p2 := Person{firstName: "Alex", lastName: "Sokolov", birthDay: time.Date(1985,time.June, 8, 8,2,5,0,time.Local)}
	p = append(p,p1)
	p = append(p,p2)
	expect = append(expect,p2)
	expect = append(expect,p1)
	p.Swap(0,1)
	if p[0] != expect[0] {
		t.Errorf(ErrT, true, false)
	}
}

func TestNewOk(t *testing.T){
	str1 := `12 23 -4
	7 5 7
	-4 1 0`
	str2 := `12 23 -4
	7 5 
	-4 1 0`
	str3 := `12 23 -4
	7 a 7
	-4 1 0`
	var expect1 error = nil
	var expect2 = "Rows need to be the same length"
	var expm *Matrix
	mat := [3][3]int {{12, 23, -4},{7, 5, 7},{ -4, 1, 0}}
	m1,er1 := New(str1)
	matrix1 := m1.Rows()
	m2,er2 := New(str2)
	m3,er3 := New(str3)
	for i := 0; i < 3; i++ {
		for j := 0; j < 3; j++{
			if  matrix1[i][j] != mat[i][j]{
				t.Errorf(ErrD, mat[i][j], matrix1[i][j])
			}
		}
	}
	if m2 != expm {
		t.Errorf("Expected: %s, got %p", expect1, m2)
	}
	if m3 != expm{
		t.Errorf("Expected: %s, got %p", expect1, m3)
	}
	if er1 != expect1 {
		t.Errorf(ErrS, expect1, er1)
	}
	if er2 == expect1 {
		t.Errorf(ErrS, expect2, er2)
	}
	if er3 == expect1 {
		t.Errorf(ErrS, expect1, er3)
	}
}

func TestRowsOk(t *testing.T) {
	str1 := `12 23 -4
	7 5 7
	-4 1 0`
	mat := [3][3]int {{12, 23, -4},{7, 5, 7},{ -4, 1, 0}}
	m1,_ := New(str1)
	matrix1 := m1.Rows()
	for i := 0; i < 3; i++ {
		for j := 0; j < 3; j++{
			if  matrix1[i][j] != mat[i][j]{
				t.Errorf(ErrD, mat[i][j], matrix1[i][j])
			}
		}
	}
}

func TestColsOk(t *testing.T) {
	str1 := `12 23 -4
	7 5 7
	-4 1 0`
	mat := [3][3]int {{12, 23, -4},{7, 5, 7},{ -4, 1, 0}}
	m1,_ := New(str1)
	matrix1 := m1.Cols()
	for i := 0; i < 3; i++ {
		for j := 0; j < 3; j++{
			if  matrix1[j][i] != mat[i][j]{
				t.Errorf(ErrD, mat[i][j], matrix1[j][i])
			}
		}
	}
}

func TestSetOk(t *testing.T){
	var b bool
	str1 := `12 23 -4
	7 5 7
	-4 1 0`
	m1,_ := New(str1)
	b = m1.Set(2,2,2)
	if b != true {
		t.Errorf(ErrT, true, b)
	}
	b = m1.Set (-2,1,2)
	if b != false {
		t.Errorf(ErrT, false, b)
	}
}