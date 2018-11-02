---
title: 'Практическое: отключить уведомления об изменении файла | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 505827d25a7e6016403567c172ad094d072f1ef3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885828"
---
# <a name="how-to-suppress-file-change-notifications"></a>Практическое: отключить уведомления об изменении файла
При изменении физического файла, представляющий текстовый буфер, откроется диалоговое окно с сообщением **вы хотите сохранить изменения следующих элементов?** Это называется уведомления об изменении файла. Если много изменений будут в файл, тем не менее, это диалоговое окно, отображающее снова и снова может быстро стать раздражает.  
  
 Программным способом, можно отключить это диалоговое окно, используя следующую процедуру. Можно подавить диалоговое окно, можно перезагрузить файл немедленно без необходимости запрашивать пользователя, чтобы сохранить изменения, каждый раз.  
  
## <a name="to-suppress-file-change-notification"></a>Чтобы отключить уведомления об изменении файла  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод, чтобы определить, какой объект текстового буфера связан с открытым файлом.  
  
2.  Прямой <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект, который в памяти, чтобы игнорировать отслеживает изменения в файлах, получая <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект (document data), а затем реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод с `fIgnore` параметр значение `true`.  
  
3.  Вызывать методы в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейсы для обновления в памяти <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект с изменения файла (например, когда поле добавляется в компонент).  
  
4.  Обновите файл на диске с учетом изменений, без учета все ожидающие изменения, которые пользователь может иметь в процессе выполнения.  
  
     Таким образом, когда <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> уведомления об изменении объекта для возобновления наблюдения за файл, текстовый буфер в памяти отражает изменения, которые вы создали. Текстовый буфер в памяти также отражает все незафиксированные изменения. Файл на диске отражают последние код, созданный вами и любые сохраненные изменения пользователем в коде изменить пользователя.  
  
5.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод для уведомления <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта для возобновления наблюдения за уведомления об изменении файла, задав `fIgnore` параметр `false`.  
  
6.  Если вы планируете внести несколько изменений в файл, как в случае управления исходным кодом (SCC), необходимо сообщить службе изменение глобальных файлов временно остановить уведомления об изменении файла.  
  
     Например если переписать файл и затем измените метку времени, уведомления об изменении файла необходимо приостановить, так как счетчик каждой из операций перезаписи и timestamp как событие изменения отдельный файл. Чтобы включить уведомления об изменении глобального файла, следует вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> метод.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как отключить уведомления об изменении файла.  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Если ваш вариант подразумевает несколько изменений в файл, как в случае SCC, затем важно для возобновления уведомления об изменении глобального файла перед уведомлением данные документа для возобновления наблюдения за изменения файлов.