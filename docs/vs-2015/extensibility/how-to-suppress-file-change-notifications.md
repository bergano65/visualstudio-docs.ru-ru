---
title: Как подавлять уведомления об изменении файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204081"
---
# <a name="how-to-suppress-file-change-notifications"></a>Практическое руководство. Отключение уведомлений об изменении файла
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При изменении физического файла, представляющего текстовый буфер, отображается диалоговое окно с сообщением **сохранить изменения в следующих элементах?** Это называется уведомлением об изменении файла. Однако если предполагается, что в файл будет внесено много изменений, это диалоговое окно может быстро оказаться нежелательным.  
  
 Можно программно отключить это диалоговое окно с помощью следующей процедуры. Таким образом можно сразу же загрузить файл, не запрашивая пользователя о необходимости сохранения изменений каждый раз.  
  
### <a name="to-suppress-file-change-notification"></a>Отключение уведомления об изменении файла  
  
1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод, чтобы определить, какой объект текстового буфера связан с открытым файлом.  
  
2. Направьте <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект, наявляющийся в памяти, для пропуска изменений файла мониторинга, получая <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта (Document Data), а затем реализуя <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод с `fIgnore` параметром, имеющим значение `true` .  
  
3. Вызывайте методы в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейсах и, чтобы обновить объект в памяти <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> с помощью изменений файла (например, при добавлении поля в компонент).  
  
4. Обновите файл на диске изменениями, не учитывая ожидающие изменения, которые могли быть выполнены пользователем.  
  
     Таким образом, когда вы направите <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект для возобновления отслеживания уведомлений об изменении файлов, текстовый буфер в памяти отражает созданные изменения, а также все остальные ожидающие изменения. Файл на диске отражает последний созданный вами код и все ранее сохраненные изменения, внесенные пользователем в коде, измененном пользователем.  
  
5. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод, чтобы уведомить <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект, чтобы возобновить отслеживание уведомлений об изменении файлов, задав `fIgnore` для параметра значение `false` .  
  
6. Если планируется внести несколько изменений в файл, как в случае с системой управления исходным кодом (SCC), необходимо сообщить службе глобального изменения файлов о необходимости временного приостановки уведомлений об изменении файлов.  
  
     Например, если перезаписать файл и затем изменить метку времени, необходимо приостановить уведомления об изменениях файлов, так как операции перезаписи и тиместампле каждого из них считаются отдельным событием изменения файла. Чтобы включить уведомление об изменении глобального файла, следует вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> метод.  
  
## <a name="example"></a>Пример  
 Ниже показано, как отключить уведомление об изменении файла.  
  
```cpp#  
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
 Если в вашем случае используется несколько изменений в файле, как в случае SCC, то важно возобновить глобальные уведомления об изменениях файлов, прежде чем получать оповещения о данных документа, чтобы возобновить отслеживание изменений в файлах.
