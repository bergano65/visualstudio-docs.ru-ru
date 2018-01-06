---
title: "Как: отключить уведомления об изменении файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 209006129bcb2cfaaf88233768df1d9597cd09a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>Как: отключить уведомления об изменении файлов
При изменении физического файла, представляющий буфер текста отображается диалоговое окно с сообщением **Вы действительно хотите сохранить изменения следующих элементов?** Это называется уведомления об изменении файла. Если предполагается, что большое количество изменений в файл, однако это диалоговое окно, снова и снова отображение может быстро стать досадных.  
  
 Программным образом, можно отключить это диалоговое окно, используя следующую процедуру. Таким образом, можно перезагрузить файл немедленно без необходимости запрашивать пользователя, чтобы сохранить изменения в каждом.  
  
### <a name="to-suppress-file-change-notification"></a>Чтобы отключить уведомления об изменении файла  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод, чтобы определить, какой объект текстового буфера связан с открытым файлом.  
  
2.  Прямой <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект, который в памяти, чтобы игнорировать контроля изменений файлов с помощью получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта (данные документа), а затем реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод с `fIgnore` параметр значение `true`.  
  
3.  Методы для класса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейсы для обновления в памяти <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект с изменениями файла (например, когда поле добавляется в компонент).  
  
4.  Применить изменения к файлу на диске без учета все ожидающие изменения, пользователь может быть в данный момент.  
  
     Таким образом, когда <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> уведомления об изменениях объекта, чтобы возобновить наблюдение за файл, текстовый буфер в памяти отражает изменения, которые создаются, а также все незафиксированные изменения. Файл на диске отражает последнюю код, сгенерированный вы и любые ранее сохраненные изменения пользователем в коде изменить пользователя.  
  
5.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод для уведомления <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта, чтобы возобновить наблюдение за уведомления об изменениях файла, задав `fIgnore` параметр `false`.  
  
6.  Если планируется внести некоторые изменения в файл, как в случае управления исходным кодом (SCC), необходимо сообщить службе изменение глобальный файл временно остановить уведомления об изменении файлов.  
  
     Например если переписать файл и затем измените метку времени, необходимо приостановить уведомления об изменениях файла, как операции перезаписи и timestample каждого считаются событие изменения в отдельном файле. Для включения уведомлений об изменении глобального файла, вместо этого следует вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> метод.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует отключение уведомления об изменении файла.  
  
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
 Если вашему обращению включает в себя несколько изменений в файле, как в случае SCC, затем важно для возобновления уведомления об изменении глобальных файлов перед уведомлением данных документа возобновить мониторинг изменений файла.