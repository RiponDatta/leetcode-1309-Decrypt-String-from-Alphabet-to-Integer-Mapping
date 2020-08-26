# leetcode 1309 - Decrypt String from Alphabet to Integer Mapping

### Approach 1
### C#
```C#
public static string FreqAlphabets(string s)
{
    var sb = new StringBuilder();
    for (int i = 0; i < s.Length; i++)
    {
        if (i + 2 < s.Length && s[i + 2] == '#')
        {
            sb.Append(Decrypt(s.Substring(i, 2)));
            i += 2;
        }
        else
            sb.Append(Decrypt(s[i].ToString()));
    }
    return sb.ToString();
}

private static char Decrypt(string str)
{
    return (char)(int.Parse(str) + 'a' - 1);
}
```
### Approach 2
### C#
```C#
public static string FreqAlphabets2(string s)
{
    var sb = new StringBuilder();
    var arr = s.Split('#');
    for (int l = 0; l < arr.Length; l++)
    {
        if (arr[l] == "") continue;
        int i = 0;
        if (l == arr.Length - 1 && s[s.Length - 1] != '#')
        {
            for (; i < arr[l].Length; i++)
            {
                sb.Append(Decrypt(arr[l][i].ToString()));
            }
        }
        else if (arr[l].Length > 2)
        {
            for (; i < arr[l].Length - 2; i++)
            {
                sb.Append(Decrypt(arr[l][i].ToString()));
            }
            sb.Append(Decrypt(arr[l].Substring(i, 2)));
        }
        else
            sb.Append(Decrypt(arr[l]));
    }
    return sb.ToString();
}
     
private static char Decrypt(string str)
{
    return (char)(int.Parse(str) + 'a' - 1);
}
```
