# mangager.py
edit_user
	no type checking
add_student
	no type checking

register_user
	name split wrong for surnames with spaces
	exceptions from brought to small

## special_facilities.py
class enumspecialfacilities
	commented out enum
	weird name
	missing exam papers in braille, text-to-speech software, TOPSPORT_STATUUT

class facilitiy
	19 != should be is not
	22 missing self arg
	get_name uses other function outside of class to get the name rather than just using a var in the class to store the name

get_special_faculities never used

weird use for facility

The different types of facilities should not be hardcoded. Instead, they should be stored in a
database such that adding and removing types of facilities is easy.

## User.py

import src.network not included in pull request

class User
	get_user_ref not found
	assert is put after assignment
	31 redundant partenteces
	41 not implemented yet

class Student
	49 use is instead of ==
	49 redundant assert, allready in var
	55 unreachable code
	64 degree attribute added later rather than in the init
	no remove facility from student
	Only admins should be able to view and modify the facilities

class Admin
	70 redundant assertion
	



other

no functions without fully typed arguments and return value