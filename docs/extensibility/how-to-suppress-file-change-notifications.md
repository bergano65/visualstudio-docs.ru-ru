---
title: "Практическое руководство: отключение уведомлений об изменении файлов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - отключить уведомления об изменении файла"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Практическое руководство: отключение уведомлений об изменении файлов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если физический файл представляет собой текстовый буфер был изменен, то откроется диалоговое окно с сообщением **Сохранить изменения к следующим элементам?** Это уведомление об изменении файла.  Если много изменений, передаются быть к файлу, однако, то это диалоговое окно, указывающее на более быстро стать еще раз и может досадным.  
  
 Можно программно отключить это диалоговое окно с помощью следующей процедуры.  С помощью этого можно перезапустить файл немедленно без запроса пользователя сохранить результаты каждый раз.  
  
### Подавление уведомление об изменении файла  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод, чтобы определить, какой объект текстового буфера связанного с открытым файлом.  
  
2.  Направьте <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект, находящийся в памяти для пропуска файл изменяется путем получения наблюдения  <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> интерфейс из  <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(объект сведений о документе\), а затем реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод с  `fIgnore` набор параметров  `true`.  
  
3.  Вызовите методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейсы для обновления расположенный в памяти  <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект с изменениями файла \(например, если поле добавлено в компонент\).  
  
4.  Обновите на диске файл в соответствии с изменениями без учета всех ожидающих правок пользователь может иметь выполняется.  
  
     Таким образом, при направите <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект к наблюдению resume для уведомлений изменения файла текстовый буфер в памяти отражает изменения, создания, так же как и любые другие ожидающие правки.  Файл на диске отражает самый последний код, созданный пользователем и все ранее сохраненные изменения пользователем в пользователь\-изменянном коде.  
  
5.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> метод, чтобы уведомить  <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект к наблюдению resume для уведомлений изменения файла путем установки  `fIgnore` параметр  `false`.  
  
6.  Если планируется внести некоторые изменения в файл, например в случае управления исходным кодом \(SCC\), то необходимо указать, что служба изменения глобального файла временно приостановлена уведомления об изменении файла.  
  
     Например, если перезаписываете файл и затем измените отметку времени, то необходимо приостановить уведомления об изменении файла, так как операции перезаписи и timestample каждый отдельный файл, как изменяются события.  Включить уведомления об изменении глобального файла необходимо вместо вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> метод.  
  
## Пример  
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
  
## Отказоустойчивость  
 Если вариант включает несколько изменений к файлу, как в случае SCC, а его важны для возобновления уведомления об изменении глобального файла до предупреждения данные документа к наблюдению resume для изменения файла.