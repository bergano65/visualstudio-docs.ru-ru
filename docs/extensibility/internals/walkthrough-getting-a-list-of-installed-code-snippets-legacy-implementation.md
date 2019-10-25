---
title: Получение списка установленных фрагментов кода (прежние версии) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 072827bbb9676ba49df5ccd69f329ea9b04c78b2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721661"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)
Фрагмент кода — это фрагмент кода, который можно вставить в исходный буфер с помощью команды меню (которая позволяет выбрать из списка установленных фрагментов кода) или выбрать ярлык фрагмента из списка завершения IntelliSense.

 Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> получает все фрагменты кода для идентификатора GUID определенного языка. Сочетания клавиш для этих фрагментов можно вставить в список завершения IntelliSense.

 Дополнительные сведения о реализации фрагментов кода в языковой службе платформы управляемых пакетов (MPF) см. [в разделе Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) .

### <a name="to-retrieve-a-list-of-code-snippets"></a>Получение списка фрагментов кода

1. В следующем коде показано, как получить список фрагментов кода для данного языка. Результаты хранятся в массиве структур <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>. Этот метод использует статический метод <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> из службы <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Однако можно также использовать поставщик услуг, предоставленный для VSPackage, и вызвать метод <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

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

### <a name="to-call-the-getsnippets-method"></a>Вызов метода snippet

1. Следующий метод показывает, как вызвать метод `GetSnippets` при завершении операции синтаксического анализа. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> вызывается после операции синтаксического анализа, которая была запущена с <xref:Microsoft.VisualStudio.Package.ParseReason> причин.

> [!NOTE]
> Список массивов `expansionsList` кэшируется по соображениям производительности. Изменения фрагментов кода не отражаются в списке до тех пор, пока служба языка не будет остановлена и перезагружена (например, при остановке и перезапуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

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

### <a name="to-use-the-snippet-information"></a>Использование данных фрагмента

1. В следующем коде показано, как использовать сведения о фрагментах кода, возвращаемые методом `GetSnippets`. Метод `AddSnippets` вызывается из средства синтаксического анализа в ответ на любые причины синтаксического анализа, которые используются для заполнения списка фрагментов кода. Это должно происходить после завершения полного синтаксического анализа в первый раз.

     Метод `AddDeclaration` создает список объявлений, которые позже отображаются в списке завершения.

     Класс `TestDeclaration` содержит все сведения, которые могут быть отображены в списке завершения, а также тип объявления.

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
- [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)