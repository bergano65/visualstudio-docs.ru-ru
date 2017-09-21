---
title: "Практическое руководство: зарегистрировать библиотеку с помощью диспетчера объектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "библиотеки, регистрация диспетчера объектов"
  - "Интерфейс IVsLibrary2, регистрация библиотеки с помощью диспетчера объектов"
  - "Интерфейс IVsSimpleLibrary2, регистрация библиотеки с помощью диспетчера объектов"
  - "Интерфейс IVsObjectManager2, регистрация библиотеки с помощью диспетчера объектов"
  - "библиотеки, средства обзора символов"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Практическое руководство: зарегистрировать библиотеку с помощью диспетчера объектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Символ\-просмотреть инструменты, например **Окно классов**"  **Обозреватель объектов**"  **Обозреватель вызовов** и  **Результаты поиска символа**, позволяют просматривать символы в проекте или во внешних компонентах.  Символы включают пространств имен, классов, интерфейсов, методов и другие элементы языка.  Библиотеки отслеживают эти символы и предоставляют их к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объекта, который заполняет средства работы с данными.  
  
 Диспетчер объекта отслеживает всех доступных библиотек.  Каждая библиотека должна зарегистрировать с помощью объекта перед защита символов для символ\-просмотря сервис.  
  
 Обычно выполняется регистрация библиотек при загрузке VSPackage.  Однако ее можно сделать на другой раз по мере необходимости.  Для отмены регистрации библиотеки, когда VSPackage завершает работу.  
  
 Чтобы зарегистрировать библиотеку, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> метод.  В случае управляемого кода, используйте библиотеки <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.  
  
 Регистрировать библиотеку, использующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.  
  
 Получить ссылку на него объекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>передайте  <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор службы  `GetService` метод.  
  
## При регистрации и отмены регистрации библиотеки с диспетчером объектов  
  
#### Регистрация библиотеки с диспетчером объектов  
  
1.  Создание библиотеки.  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> введите и вызовите  <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> метод.  
  
    ```vb#  
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
  
    ```c#  
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
  
#### Отмена регистрации библиотеки с диспетчером объектов  
  
1.  Получите ссылку на объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> введите и вызовите  <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> метод.  
  
    ```vb#  
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
  
    ```c#  
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
  
## См. также  
 [Расширяемость устаревших языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Практическое руководство: предоставлять список символов, предоставленный библиотекой диспетчера объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)