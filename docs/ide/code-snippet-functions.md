---
title: "Функции фрагмента кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "фрагменты кода [Visual Studio], функции"
  - "фрагменты кода IntelliSense, функции"
  - "фрагменты [Visual Studio], функции"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Функции фрагмента кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для использования с фрагментами кода [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] доступно три функции.  Функции указаны в элементе [Function](http://msdn.microsoft.com/ru-ru/572c5549-5821-4e15-8ecd-0fa86c1c65df) фрагмента кода.  Дополнительные сведения о создании фрагментов кода см. в разделе [Фрагменты кода](../ide/code-snippets.md).  
  
## Функции  
 В следующей таблице описаны функции, которые можно использовать с элементом `Function` во фрагментах кода.  
  
|Функция|Описание|Язык|  
|-------------|--------------|----------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Генерирует оператор SWITCH и набор операторов CASE для членов перечисления, указанных параметром `EnumerationLiteral`.  Параметр `EnumerationLiteral` должен быть ссылкой на литерал перечисления или тип перечисления.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Возвращает имя класса, содержащего вставленный код.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Сокращает параметр *TypeName* до его простой формы в контексте, в котором был вызван фрагмент кода.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## Пример  
 В следующем примере показан способ использования функции `GenerateSwitchCases`.  При вставке этого фрагмента и при вводе перечисления в литерал `$switch_on$`, литерал `$cases$` создает оператор `case` для каждого значения в перечислении.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Пример  
 В следующем примере показан способ использования функции `ClassName`.  При вставке этого фрагмента литерал `$classname$` заменяется именем включающего класса в этом положении в файле кода.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Пример  
 В следующем примере показан способ использования функции `SimpleTypeName`.  При вставке этого фрагмента в файл кода, литерал `$SystemConsole$` будет заменен самой простой формой типа <xref:System.Console> в контексте, в котором был вызван фрагмент.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## См. также  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/ru-ru/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)