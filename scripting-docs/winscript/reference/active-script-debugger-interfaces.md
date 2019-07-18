---
title: Интерфейсы отладчика активных скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed8ff0361396deaaffd46f14ca1fc38869988593
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422460"
---
# <a name="active-script-debugger-interfaces"></a>Интерфейсы отладчика активных скриптов
Файлы заголовков activdbg.h и activdbg100.h предоставляют интерфейсы, перечисления и структуры, перечисленные в этом разделе. Они предназначены для отладки скрипта.  
  
> [!NOTE]
> `IJSDebug*` Интерфейсы и `IEnumJsStackFrames` интерфейс сначала были выпущены в Internet Explorer 11 для отладки машинного кода с помощью скрипта. Файл заголовка для этих интерфейсов является jscript9diag.h.  
  
## <a name="in-this-section"></a>В этом разделе  
 Следующие интерфейсы отладки не зависящий от языка, зависящий от узла:  
  
- [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [Интерфейс IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [Интерфейс IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [Интерфейс IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [Интерфейс IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
  
- [Интерфейс IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)  
  
- [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [Интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [Интерфейс IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [Интерфейс IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [Интерфейс IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)  
  
- [Интерфейс IDebugDocument](../../winscript/reference/idebugdocument-interface.md)  
  
- [Интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [Интерфейс IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [Интерфейс IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [Интерфейс IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [Интерфейс IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
  
- [Интерфейс IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [Интерфейс IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)  
  
- [Интерфейс IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
  
- [Интерфейс IDebugSessionProvider](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [Интерфейс IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)  
  
- [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [Интерфейс IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [Интерфейс IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [Интерфейс IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [Интерфейс IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [Интерфейс IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [Интерфейс IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [Интерфейс IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [Интерфейс IJsDebug](../../winscript/reference/ijsdebug-interface.md)  
  
- [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [Интерфейс IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [Интерфейс IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [Интерфейс IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [Интерфейс IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [Интерфейс IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [Интерфейс IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [Интерфейс IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx Interface](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [Интерфейс IRemoteDebugApplicationThreadEx](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [Интерфейс ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)  
  
- [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [Интерфейс IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [Интерфейс IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  В следующем разделе перечислены константы, перечисления и структуры, используемые для отладки:  
  
- [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>См. также  
 [Обзор отладки активных скриптов](../../winscript/active-script-debugging-overview.md)