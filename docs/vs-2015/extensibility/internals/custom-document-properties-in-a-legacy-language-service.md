---
title: Настраиваемые свойства документа в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2062932f5c9b0c1d51b0503742f7387b7da3dec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992682"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Настраиваемые свойства документа в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Свойства документа, которые могут отображаться в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **свойства** окна. Языки программирования обычно не имеют свойства, связанные с отдельным исходных файлов. Тем не менее XML поддерживает свойства документа, которые влияют на кодирование, схемы и таблицы стилей.  
  
## <a name="discussion"></a>Обсуждение  
 Если ваш язык должен настраиваемые свойства документа, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса и реализовать необходимые свойства для производного класса.  
  
 Кроме того свойства документа обычно хранятся в самом файле источника. Служба языка для анализа информации о свойство из исходного файла для отображения в **свойства** окна и обновления исходного файла, при внесении изменений в свойства документа в  **Свойства** окна.  
  
## <a name="customizing-the-documentproperties-class"></a>Настройка класса DocumentProperties  
 Для поддержки настраиваемых свойств документа, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса и добавьте произвольному количеству свойств. Необходимо также предоставить пользовательские атрибуты, чтобы упорядочить их в **свойства** Отображение окна. Если свойство имеет только `get` метод доступа, он отображается только для чтения в **свойства** окна. Если свойство имеет и `get` и `set` методы доступа, свойство также может быть обновлено в **свойства** окна.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример класса, производного от <xref:Microsoft.VisualStudio.Package.DocumentProperties>, показывающая два свойства: имя файла и описание. При обновлении свойства, пользовательский метод на <xref:Microsoft.VisualStudio.Package.LanguageService> вызывается для записи свойства исходного файла.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiating-the-custom-documentproperties-class"></a>Создавая экземпляр класса Custom DocumentProperties  
 Для создания экземпляра класса свойства настраиваемого документа, следует переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> метод в вашей версии <xref:Microsoft.VisualStudio.Package.LanguageService> класса для возвращения одного экземпляра вашего <xref:Microsoft.VisualStudio.Package.DocumentProperties> класса.  
  
### <a name="example"></a>Пример  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>Свойства в исходном файле  
 Так как свойства документа обычно относятся к исходному файлу, значения хранятся в самом файле источника. Это требует поддержки средства синтаксического анализа языка или средства проверки для определения этих свойств. Например свойства документа XML хранятся в корневом узле. Изменяются значения в корневом узле, когда **свойства** значения окно, изменяются, и корневой узел обновляется в редакторе.  
  
### <a name="example"></a>Пример  
 В этом примере хранит свойства «Filename» и «Description» в первые две строки исходного файла, внедренных в заголовке специальный комментарий, как:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 В этом примере показано два метода, необходимые для получения и задания свойства документа из исходного файла, а также первые две строки, как свойства обновляются в том случае, если пользователь изменяет исходный файл напрямую. `SetPropertyValue` Метод в примере, показанном ниже одинаков вызван один из `TestDocumentProperties` класса, как показано в разделе «Настройка класса DocumentProperties».  
  
 В этом примере использует сканер для определения типа маркеров в первые две строки. Данный пример является только для иллюстративных целей. Более типичный подход к этой ситуации — разбор исходного файла в то, что называется дерево синтаксического анализа, где каждый узел дерева содержит сведения об определенном токене. Корневой узел будет содержать свойства документа.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
