<h2> Hi, I'm Lars Stalder! <img src="https://media.giphy.com/media/mGcNjsfWAjY5AEZNw6/giphy.gif" width="50"></h2>

```sql
DROP TYPE t_dev FORCE;
/

CREATE TYPE t_dev AS OBJECT (
  name   VARCHAR2(50),
  role   VARCHAR2(50),
  langs  SYS.ODCIVARCHAR2LIST,
  MEMBER PROCEDURE say_hi
);
/

CREATE TYPE BODY t_dev AS
  MEMBER PROCEDURE say_hi IS
    l_langs VARCHAR2(4000);
  BEGIN
    SELECT LISTAGG(COLUMN_VALUE, ', ')
             WITHIN GROUP (ORDER BY COLUMN_VALUE)
      INTO l_langs
      FROM TABLE(SELF.langs);

    DBMS_OUTPUT.PUT_LINE('👋 Hi! I''m ' || name || ', your friendly ' || role || '.');
    DBMS_OUTPUT.PUT_LINE('🌍 I speak: ' || NVL(l_langs, '(none)'));
    DBMS_OUTPUT.PUT_LINE('☕ Coffee level: OVER 9000.');
  END;
END;
/

DECLARE
  me t_dev := t_dev(
    'Lars Stalder',
    'Database App Developer',
    SYS.ODCIVARCHAR2LIST('de_CH','en_GB','fr_CH')
  );
BEGIN
  me.say_hi;
END;
/
```

## 🗂️ Highlight Projects

<a href="[https://github.com/Zhenye-Na/DA-RNN](https://github.com/LordofCoding06/LordofCoding06)">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=LordofCoding06&repo=LordofCoding06&show_icons=true&line_height=27&title_color=6aa6f8&text_color=8a919a&icon_color=6aa6f8&bg_color=22272e" alt="LordofCoding06" />
</a>

<a href="https://github.com/Zhenye-Na/crnn-pytorch">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=LordofCoding06&repo=M324-Aufgabe-2-Git-Hooks&show_icons=true&line_height=27&title_color=6aa6f8&text_color=8a919a&icon_color=6aa6f8&bg_color=22272e" alt="M324-Aufgabe-2-Git-Hooks" />
</a>

## 📊 Stats
![](https://github-readme-stats.vercel.app/api?username=LordofCoding06&theme=dark&hide_border=false&include_all_commits=false&count_private=false)
