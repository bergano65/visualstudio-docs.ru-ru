---
title: Практическое руководство. Зарегистрировать библиотеку с помощью диспетчера объектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7481b9710237bcd1e624b07f8985b5708f271bef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312053"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Практическое руководство. Зарегистрировать библиотеку с диспетчером объектов
Просмотр символы средства, такие как **представление классов**, **обозреватель объектов**, **Обозреватель вызовов** и **результаты поиска символа**, позволяют просматривать символы в проекте или на внешние компоненты. Символы включают пространства имен, классы, интерфейсы, методы и другие элементы языка. Библиотеки отслеживать эти символы и представлять их в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов, которое заполняет средства с данными.

 Диспетчер объектов хранит информацию о всех доступных библиотек. Каждой библиотеки необходимо зарегистрировать с диспетчером объектов, прежде чем предоставлять символы для средства просмотра символов.

 Как правило при загрузке VSPackage регистрации библиотеки. Тем не менее это можно сделать позже, при необходимости. Отменить регистрацию библиотеки выключением VSPackage.

 Чтобы зарегистрировать библиотеку, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> метод. Библиотеку управляемого кода используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.

 Чтобы отменить регистрацию библиотеки, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.

 Для получения ссылки на диспетчер объектов, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор для службы `GetService` метод.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Регистрировать и отменять регистрацию библиотеки с диспетчером объектов

### <a name="to-register-a-library-with-the-object-manager"></a>Чтобы зарегистрировать библиотеку с диспетчером объектов

1. Создание библиотеки.

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

2. Получить ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> введите и вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Чтобы отменить регистрацию библиотеки с диспетчером объектов

1. Получить ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> введите и вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.

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
- [Расширяемость устаревший языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Поддержка средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Практическое руководство. Раскрывать списки символов, предоставляемые библиотекой в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)