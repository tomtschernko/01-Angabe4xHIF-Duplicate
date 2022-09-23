# 01-Angabe4xHIF-Duplicate
## Aufgabe:
Siehe auch: Dateidubletten aufspüren – Clean Code Developer School (ccd-school.de)

Entwickle eine Bibliothek, mit der man Dateidubletten in einem Verzeichnisbaum finden kann.
Der Kontrakt der Bibliothek sollte so aussehen:

```code
public interface IDuplicateCheck
{
    IEnumerable<IDuplicate> Collect(string path);
    IEnumerable<IDuplicate> Collect(string path, );

}
public interface IDuplicate
{
    IEnumerable<string> FilePath { get; }
}
public enum CollectMode
{
    SizeOnly,
    SizeAndName,
    SizeAndNameAndFirstThree

}

```


Zuerst wird die Methode Collect aufgerufen. Sie durchläuft alle Dateien in einem Verzeichnisbaum und vergleicht Dateien nur sehr grob. Standardmäßig werden Dateiname und -größe verglichen, auf Wunsch aber auch nur die Dateigröße. Dateien, die danach für gleich gehalten werden, liefert die Funktion als IDuplicate zurück.
In einem zweiten Pass werden dann potenzielle Dubletten auf ihre tatsächliche Gleichheit geprüft. 

## Variation 1
Jetzt wird der komplette Inhalt repräsentiert durch einen [MD5 Hash] verglichen. Dateien, die nun gleich sind, werden wieder als IDublette zurückgeliefert [1].

## Ressourcen
- [MD5 Hash](http://de.wikipedia.org/wiki/Message-Digest_Algorithm_5)
- [Calculates the total size of files in a directory](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop)
- [Iterate File Directories with the Parallel Class](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class)
