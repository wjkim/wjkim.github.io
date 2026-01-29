---
title: "C# 파일 압축 및 해제 방법"
date: "2026-01-29T15:01:35+09:00"
layout: "post"
description: >

cover: "/images/posts/How_to_compress_and_decompress_a_file_in_CS_compres_512.png"
thumbnail: ""
categories: ["Programming"]
tags: ["CSharp", "Compression"]
---

파일 압축 및 해제는 C#에서 기본적으로 제공하는 함수를 사용하면 됩니다.

참조에 System.IO.Compression 을 추가 해주면 사용 가능합니다.

```csharp
using System; 
using System.IO.Compression;  

class  Program { static  void  Main(string[] args) 
{ 
    // 압축 파일 폴더는 대상 폴더와 같은 위치면 안됨  
    string compressFileName =  @".\compress\zipFile.zip"; 
    string sourceFilePath =  @".\zipFileFolder"; 
    string extractPath =  @".\extract";
    CompresstionFile(sourceFilePath, compressfileName);  
    ExtractToDirectory(compressFileName, extractPath);  

    private  void  CompresstionFile(string sourceDirectoryName, string archiveFileName)  
    {  
        try  
        {  
            FileInfo fileinfo =  new FileInfo(archiveFileName);  
            if  (!fileinfo.Exists)  
            {  
                ZipFile.CreateFromDirectory(sourceDirectoryName,  archiveFileName);  
            }  
        }  
        catch  (ArgumentException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 "  +  "destinationArchiveFileName은 공백만 있는 Empty이거나 잘못된 문자가 하나 이상 있는 경우입니다.");  
        }  
        catch  (PathTooLongException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 destinationArchiveFileName에서 지정된 경로, 파일 이름 또는 " +  "둘 다가 시스템에 정의된 최대 길이를 초과하는 경우");  
        }  
        catch  (DirectoryNotFoundException ex)  
        {  
            MessageBox.Show("sourceDirectoryName이 잘못되었거나 존재하지 않는 경우"  +  "(예: 매핑되지 않은 드라이브의 경로를 지정한 경우)");  
        }  
        catch  (IOException ex)  
        {  
            MessageBox.Show("destinationArchiveFileName가 이미 있는 경우 or "  +  "지정된 디렉터리의 파일을 열 수 없는 경우 or 보관할 파일을 여는 동안 I/O 오류가 발생했습니다.");  
        }  
        catch  (UnauthorizedAccessException ex)  
        {  
            MessageBox.Show("destinationArchiveFileName은 디렉터리를 지정합니다. or "  +  "호출자에게는 sourceDirectoryName에서 지정된 디렉터리에 액세스하기 위한 필수 권한이 없거나 "  +  "destinationArchiveFileName에 지정된 파일이 없습니다.");  
        }  
        catch  (NotSupportedException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 destinationArchiveFileName에 잘못된 형식이 포함되어 있는 경우 or "  +  "zip 보관 위치가 쓰기를 지원하지 않는 경우");  
        }  
        catch  (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
        }  
    }  

    private  void  ExtractToDirectory(string sourceArchiveFileName,  string directoryName)  
    {  
        try  
        {  
            FileInfo fileinfo =  new FileInfo(sourceArchiveFileName);  
            if  (fileinfo.Exists)  
            {  
                ZipFile.ExtractToDirectory(sourceArchiveFileName,  directoryName);  
            }  
        }  
        catch  (ArgumentException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 "  +  "destinationArchiveFileName은 공백만 있는 Empty이거나 잘못된 문자가 하나 이상 있는 경우입니다.");  
        }  
        catch  (PathTooLongException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 destinationArchiveFileName에서 지정된 경로, 파일 이름 또는 "  +  "둘 다가 시스템에 정의된 최대 길이를 초과하는 경우");  
        }  
        catch  (DirectoryNotFoundException ex)  
        {  
            MessageBox.Show("sourceDirectoryName이 잘못되었거나 존재하지 않는 경우"  +  "(예: 매핑되지 않은 드라이브의 경로를 지정한 경우)");  
        }  
        catch  (IOException ex)  
        {  
            MessageBox.Show("destinationArchiveFileName가 이미 있는 경우 or "  +  "지정된 디렉터리의 파일을 열 수 없는 경우 or 보관할 파일을 여는 동안 I/O 오류가 발생했습니다.");  
        }  
        catch  (UnauthorizedAccessException ex)  
        {  
            MessageBox.Show("destinationArchiveFileName은 디렉터리를 지정합니다. or "  +  "호출자에게는 sourceDirectoryName에서 지정된 디렉터리에 액세스하기 위한 필수 권한이 없거나 "  +  "destinationArchiveFileName에 지정된 파일이 없습니다.");  
        }  
        catch  (NotSupportedException ex)  
        {  
            MessageBox.Show("sourceDirectoryName 또는 destinationArchiveFileName에 잘못된 형식이 포함되어 있는 경우 or "  +  "zip 보관 위치가 쓰기를 지원하지 않는 경우");  
        }  
        catch  (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
        }  
    }
```