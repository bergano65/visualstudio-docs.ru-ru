---
title: 'Как: Зарегистрируйте библиотеку у диспетчера объектов (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707946"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Как: Регистрация библиотеки у диспетчера объектов
Инструменты просмотра символов, такие как **Class View,** **Object Browser,** **Call Browser** и **«Найти результаты символов»,** позволяют просматривать символы в проекте или во внешних компонентах. Символы включают пространства имен, классы, интерфейсы, методы и другие языковые элементы. Библиотеки отслеживают эти символы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и разоблачают их диспетчеру объектов, который заполняет инструменты данными.

 Диспетчер объектов отслеживает все доступные библиотеки. Каждая библиотека должна зарегистрироваться у диспетчера объектов, прежде чем предоставить символы для инструментов просмотра символов.

 Как правило, вы регистрируете библиотеку при загрузке VSPackage. Тем не менее, это может быть сделано в другое время по мере необходимости. Вы отрегистрируете библиотеку при закрытии VSPackage.

 Для регистрации библиотеки <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> воспользуйтесь методом. Для управляемой библиотеки <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> кода используйте метод.

 Чтобы отменить регистрацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> библиотеки, используйте метод.

 Чтобы получить ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>диспетчера <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> объекта, `GetService` передайте идентификатор службы методу.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Регистрация и отменить библиотеку у диспетчера объектов

### <a name="to-register-a-library-with-the-object-manager"></a>Регистрация библиотеки у диспетчера объектов

1. Создайте библиотеку.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Получите ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> объект типа <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> и позвоните по методу.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Отменить библиотеку с диспетчером объектов

1. Получите ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> объект типа <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> и позвоните по методу.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>См. также
- [Расширяемость устаревшей языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Поддержка инструментов просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Как: Выставлять списки символов, предоставленных библиотекой диспетчеру объекта](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
