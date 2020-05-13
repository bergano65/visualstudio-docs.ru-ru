---
title: Получение списка установленных фрагментов кода (Наследие) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703655"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)
Фрагмент кода — это фрагмент кода, который может быть вставлен в исходный буфер либо с командой меню (что позволяет выбрать среди списка установленных фрагментов кода), либо путем выбора фрагмента ярлыка из списка завершения IntelliSense.

 Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> получает все фрагменты кода для определенного языка GUID. Ярлыки для этих фрагментов могут быть вставлены в список завершения IntelliSense.

 Подробную информацию о реализации фрагментов кода в языковой службе управляемого пакета (MPF) можно просмотреть в службе поддержки [фрагментов кода в Программе Legacy Language Service.](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

### <a name="to-retrieve-a-list-of-code-snippets"></a>Для получения списка фрагментов кода

1. Следующий код показывает, как получить список фрагментов кода для данного языка. Результаты хранятся в <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> массиве структур. Этот метод использует <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> статический <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> метод, <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> чтобы получить интерфейс от службы. Тем не менее, вы также можете использовать поставщика <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> услуг, предоставленных вашему VSPackage и вызвать метод.

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

### <a name="to-call-the-getsnippets-method"></a>Вызов метода GetSnippets

1. Следующий метод показывает, `GetSnippets` как вызвать метод по завершении операции разбора. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> называется после операции разбора, которая была <xref:Microsoft.VisualStudio.Package.ParseReason>начата с причиной.

> [!NOTE]
> Список `expansionsList` массивов кэшируется по причинам производительности. Изменения в фрагментах не отражаются в списке до тех пор, пока языковая служба не [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]будет остановлена и перезагружена (например, путем остановки и перезапуска).

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

### <a name="to-use-the-snippet-information"></a>Использовать информацию о фрагментах

1. В следующем коде показано, как использовать информацию фрагмента, возвращенную методом. `GetSnippets` Метод `AddSnippets` вызывается из парсера в ответ на любую причину разбора, которая используется для заполнения списка фрагментов кода. Это должно происходить после того, как полный разбор был сделан в первый раз.

     Метод `AddDeclaration` создает список деклараций, который позже отображается в списке завершения.

     Класс `TestDeclaration` содержит всю информацию, которая может быть отображана в списке завершения, а также тип декларации.

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
