---
title: "Реализация вспомогательных интерфейсов промежуточных узлов | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Вспомогательные интерфейсы промежуточных узлов, реализация"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Реализация вспомогательных интерфейсов промежуточных узлов
Интерфейс [Интерфейс IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) значительно упрощает задачу создания промежуточный узел для активной отладки, поскольку он предоставляет реализации для многих интерфейсов, необходимых для умного размещения.  
  
 Чтобы быть промежуточным узлом, используя `IDebugDocumentHelper`, ведущее приложение должно сделать только 3 действия:  
  
1.  Диспетчер процесса `CoCreate` отладка и использует интерфейс [Интерфейс IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) чтобы добавить приложение к списку debuggable приложений.  
  
2.  Создание вспомогательного метода документа отладки для каждого объекта скрипта, используя метод [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  Убедитесь, что указаны имя документа, родительский документ, текст и блоки скрипта.  
  
3.  Реализуйте интерфейс [Интерфейс IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) на объекте, что средства интерфейс [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) \(который обязателен для активного скрипта\).  Единственный нестандартный метод на делегатах интерфейса `IActiveScriptSiteDebug` просто к вспомогательному приложению.  
  
 При необходимости основное приложение может реализовывать интерфейс [Интерфейс IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) если для этого требуется дополнительный элемент управления по цвету синтаксиса, облегчающие создание контекста документа, а второй расширенной функциональностью.  
  
 Основное ограничение вспомогательном приложении промежуточного узла, что он может обрабатывать только документы, содержимое которых изменяются или уменьшена после того, как они были добавитьы \(хотя документы могут развернуть\).  Для многих промежуточных узлов, однако она предоставляет функциональность точно, что требуется.  
  
 В следующих разделах описывается каждый шаг подробно.  
  
## Создайте объект приложения  
 Прежде чем вспомогательный объект промежуточного узлов можно использовать, необходимо создать объект [Интерфейс IDebugApplication](../winscript/reference/idebugapplication-interface.md) для представления приложения в отладчике.  
  
#### Создать объект приложения  
  
1.  Создайте экземпляр процесса с помощью `CoCreateInstance` диспетчер отладки.  
  
2.  Вызов метода [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Задайте имя в приложении с помощью [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Добавьте объект приложения в список debuggable приложений с помощью [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Код под структурами процесс, но он не включают проверку ошибок и другие техники предположительно программирования.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## Использование IDebugDocumentHelper  
  
#### Использование вспомогательного метода \(минимальная последовательность шагов\)  
  
1.  Для каждого документа узла, создание вспомогательного метода с помощью [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Вызовите [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) во вспомогательном приложении, задающего имя, атрибуты документа и т д  
  
3.  Вызовите службу [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) с родительским приложением для документа \(или значение null, если документ корневой элемент\), то для определения позиции документа в дереве и сделать его видимым в отладчике.  
  
4.  Вызовите [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) или [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) для определения текста документа.  \(Эти можно вызывать несколько раз, если документ загрузить инкрементно, как в случае с браузерами\).  
  
5.  Вызов [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) для указания диапазона для каждого блока скрипта и связанных обработчиков скриптов.  
  
## Реализация IActiveScriptSiteDebug  
 Реализация [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), получает вспомогательный объект, соответствующий заданному сайту, а затем получает начальное смещение документа для данного контекста источника следующим образом:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Далее используйте вспомогательный метод для создания нового документа указанный контекст для смещения символов:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Для реализации [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), просто вызовите `IDebugApplication::GetRootNode` \(унаследованном из [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\).  
  
 Для реализации [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), просто возвращать `IDebugApplication` первоначальном создан с помощью диспетчера процесс отладки.  
  
## Необязательный интерфейс IDebugDocumentHost  
 Основное приложение может предоставить реализацию [Интерфейс IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) с помощью [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) чтобы присвоить ей дополнительный элемент управления через службу приложением.  Ниже приведены некоторые из ключевых факторов интерфейс основного приложения позволяет сделать:  
  
-   Добавление текста с использованием [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md), что узлу не требуется предоставить действительные символы немедленно.  Если символы действительно необходимы, будут вызывать [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) вспомогательного приложения на узле.  
  
-   Переопределите по умолчанию расцветка синтаксиса службу, предоставляемая приложением.  Вспомогательный метод вызывает [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) для определения расцветку для диапазона символов, метод обратного западения в своей реализации по умолчанию если извлечение `E_NOTIMPL` основного приложения.  
  
-   Обеспечьте управление неизвестно для контекстов документа, созданных с помощью [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md) службу приложением.  Это позволяет основному приложению переопределить возможность реализации контекста документа по умолчанию.  
  
-   Введите путь в файловой системе для документа.  Некоторые при отладке использование UIs это позволить пользователю изменить и сохранить изменения в документе.  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) Позвонитьо для уведомления основного приложения после того как документ был сохранен.  
  
## См. также  
 [Обзор отладки активных скриптов](../winscript/active-script-debugging-overview.md)