```python
Rule {
	Initiatior {
		Match PROCESS {
			Exclue USER_SID { -v "S-1-5-21-3072787181-3674142334-3500518665-1105" }
		}
	}
	Target {
		Match PROCESS {
			Include OBJECT_NAME { -v "powershell.exe" }
			Include ACCESS_MASK { -v "CREATE" }
		}
	}
}
```

