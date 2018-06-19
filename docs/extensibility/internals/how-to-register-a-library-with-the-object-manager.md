---
title: 'Как: регистрации библиотеки с помощью диспетчера объектов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 30bf2775c358b107fe299f0d60bc00a2030465e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132999"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Как: регистрации библиотеки с помощью диспетчера объектов
Просмотр символов такие средства, как **представление классов**, **обозревателя объектов**, **обозревателя вызовов** и **результаты поиска символа**, позволяют просматривать символы в проекте или в внешние компоненты. Символы включают пространства имен, классы, интерфейсы, методы и другие элементы языка. Библиотеки отслеживать эти символы и предоставлять их [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объектов, которое заполняет средства с данными.  
  
 Диспетчер объектов сохраняет сведения о всех доступных библиотек. Прежде чем предоставить символы для средств просмотра символ диспетчер объектов необходимо зарегистрировать каждой библиотеки.  
  
 Как правило при загрузке VSPackage регистрации библиотеки. Однако он может быть выполнена позже при необходимости. Отменить регистрацию библиотеки выключением VSPackage.  
  
 Чтобы зарегистрировать библиотеку, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> метод. В случае управляемого кода библиотеки, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.  
  
 Чтобы отменить регистрацию библиотеки, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.  
  
 Для получения ссылки на диспетчер объектов, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор для службы `GetService` метод.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Регистрация и Отмена регистрации библиотеки с помощью диспетчера объектов  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Чтобы зарегистрировать библиотеку в диспетчер объектов  
  
1.  Создание библиотеки.  
  
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
  
2.  Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> типа и вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.  
  
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
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Отменить регистрацию библиотеки диспетчера объектов  
  
1.  Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> типа и вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.  
  
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
 [Расширяемость устаревших языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Вспомогательные средства обзора символ](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)