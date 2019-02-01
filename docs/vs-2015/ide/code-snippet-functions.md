---
title: Функции фрагментов кода | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 95ee6a99a069f81a2e63c5bbe11186afaf773423
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790011"
---
# <a name="code-snippet-functions"></a>Функции фрагмента кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С фрагментами кода [!INCLUDE[csprcs](../includes/csprcs-md.md)] можно использовать три функции. Функции указываются в элементе [Function](http://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) фрагмента кода. Сведения о создании фрагментов кода см. в разделе [Фрагменты кода](../ide/code-snippets.md).  
  
## <a name="functions"></a>Функции  
 Следующая таблица описывает функции, доступные для использования с элементом `Function` во фрагментах кода.  
  
|Функция|Описание|Язык|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Формирует оператор switch и набор операторов case для членов перечисления, заданных параметром `EnumerationLiteral`. Параметр `EnumerationLiteral` должен быть ссылкой на литерал перечисления или тип перечисления.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`ClassName()`|Возвращает имя класса, содержащего вставленный фрагмент кода.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Редуцирует параметр *TypeName* до его простейшей формы в контексте, в котором был вызван фрагмент.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать функцию `GenerateSwitchCases`. При вставке данного фрагмента и вводе перечисления в литерал `$switch_on$` литерал `$cases$` создает оператор `case` для каждого значения в перечислении.  
  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать функцию `ClassName`. При вставке этого фрагмента литерал `$classname$` заменяется именем включающего класса в этом месте файла кода.  
  
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
  
## <a name="example"></a>Пример  
 Этот пример показывает, как использовать функцию `SimpleTypeName`. При вставке этого фрагмента в файл кода литерал `$SystemConsole$` заменяется простейшей формой типа <xref:System.Console> в контексте, в котором фрагмент был вызван.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Элемент Function (фрагменты кода IntelliSense)](http://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)
