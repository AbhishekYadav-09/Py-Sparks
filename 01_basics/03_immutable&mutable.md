Immutable → int, float, str, tuple, bool, frozenset

Mutable → list, dict, set, bytearray


username = "abhi"
new_user = username

print(username)  # abhi
print(new_user)  # abhi

username = "yadav"  # naya object ban gaya

print(username)  # yadav
print(new_user)  # abhi



Memory me ek string object "abhi" banega (string immutable hai).
username us object ka reference hold karega.
Matlab username → "abhi"

Yahan naya object create nahi hota.
Bas new_user bhi "abhi" wale object ko point karega.
Matlab ab do references same object par:
username → "abhi" ← new_user

Kyunki string immutable hai → modify nahi ho sakta.
Isliye "yadav" naam ka naya object memory me create hoga.
Ab username "yadav" ko point karega.
Lekin new_user abhi bhi purane "abhi" ko point karega.

Agar "abhi" ko koi bhi reference point nahi karega, to woh garbage collection ke zariye free ho jayega.
Lekin abhi new_user usko point kar raha hai, isliye "abhi" abhi memory me rahega.