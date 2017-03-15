---
title: "Получение списка установлен фрагменты кода (устаревшая версия) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: d49d5eb1a6a2e045d477dd03fba9372123cae83a
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Пошаговое руководство: Получение списка установленных текстов (реализация прежних версий)
Фрагмент кода — это часть кода, могут быть вставлены в исходный буфер с помощью команды меню (что позволяет, задав список фрагментов кода установленных) или путем выбора из списка завершения IntelliSense ярлык фрагмента.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>Метод возвращает все фрагменты кода для конкретного языка GUID.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Ярлыки для этих фрагментов могут быть вставлены в списке завершения IntelliSense.  
  
 В разделе [поддержка фрагментов кода в языковую службу для прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) подробные сведения о реализации фрагменты кода в управляемых пакетов языковую службу framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Чтобы получить список фрагментов кода  
  
1.  Следующий код показывает, как получить список фрагментов кода для данного языка. Результаты сохраняются в массив <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>структуры.</xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> Этот метод использует статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>метод, чтобы получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>службы.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Тем не менее, можно использовать поставщик службы VSPackage и вызов <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>метод.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>  
  
    ```c#  
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
  
1.  Следующий метод показан порядок вызова `GetSnippets` метод по завершении выполнения операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>Метод вызывается после операции синтаксического анализа, который был запущен с Причина <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>  
  
> [!NOTE]
>  `expansionsList` Массив listis кэширования для повышения производительности. Изменения фрагменты не отражаются в списке, пока не будет остановлена и перезагружена языковую службу (например, путем остановки и перезапуска [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```c#  
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
  
### <a name="to-use-the-snippet-information"></a>Чтобы использовать фрагмент информацию  
  
1.  Ниже показано использование фрагмента информацию, возвращаемую `GetSnippets` метод. `AddSnippets` Метод вызывается из средства синтаксического анализа в ответ на какой-либо причине синтаксического анализа, который используется для заполнения списка фрагментов кода. Это должно выполняться после завершения полной обработки в первый раз.  
  
     `AddDeclaration` Метод формирует список объявлений, отображается в списке завершения позже.  
  
     `TestDeclaration` Класс содержит все сведения, которые могут отображаться в список завершения, а также тип объявления.  
  
    ```c#  
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
 [Поддержка фрагментов кода в языковую службу для прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
