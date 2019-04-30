---
title: Пошаговое руководство. Получение списка установлены фрагменты кода (реализация прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 256430c0e41bfc0452282c89407335d997cc715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440761"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Пошаговое руководство. Получение списка установленных фрагментов кода (реализация прежних версий)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Фрагмент кода — это часть кода, который может быть вставлен в исходный буфер с помощью команды меню (что позволяет, задав список фрагментов кода) или путем выбора из списка завершения IntelliSense ярлык фрагмента.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Метод возвращает все фрагменты кода для конкретного языка GUID. Сочетания клавиш для этих фрагментов могут быть вставлены в списке завершения IntelliSense.  
  
 См. в разделе [поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) Дополнительные сведения о реализации фрагменты кода в языковой службе управляемых пакетов framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Для получения списка фрагментов кода  
  
1. Ниже показано, как получить список фрагментов кода для данного языка. Результаты будут храниться в массиве <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> структуры. Этот метод использует статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод для получения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службы. Тем не менее, можно также использовать поставщик служб, заданный для VSPackage и вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> метод.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Для вызова метода GetSnippets  
  
1. Следующий метод отображает порядок вызова `GetSnippets` метод при завершении операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Был вызван после операции синтаксического анализа, которая была запущена с указанием причины <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
> `expansionsList` Массива listis кэширования для повышения производительности. Фрагменты кода изменения не отражаются в списке, пока не будет остановлена и перезагружена языковой службы (например, остановив и перезапустив [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Использовать сведения о фрагменте  
  
1. Приведенный ниже показано, как использовать фрагмент сведений, полученных `GetSnippets` метод. `AddSnippets` Метод вызывается из синтаксического анализатора в ответ на какой-либо причине синтаксического анализа, который используется для заполнения списка фрагментов кода. Это должно выполняться после завершения полного синтаксического анализа в первый раз.  
  
     `AddDeclaration` Метод формирует список объявлений, более поздней версии отображается в списке завершения.  
  
     `TestDeclaration` Класс содержит все данные, которые могут отображаться в списке завершения, а также тип объявления.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
