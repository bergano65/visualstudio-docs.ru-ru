---
title: Информация HRESULT в управляемом коде | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: b629f856bcdba13523c094b5d3fd32b6848ec23f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256078"
---
# <a name="hresult-information-in-managed-code"></a>Информация HRESULT в управляемом коде
В процессе взаимодействия между управляемым кодом и моделью COM могут возникать проблемы, если возвращаются значения HRESULT.  
  
 В COM-интерфейсе возвращаемое значение HRESULT может выполнять следующие функции:  
  
-   предоставлять сведения об ошибке (например, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>);  
  
-   предоставлять сведения о состоянии нормального выполнения программы.  
  
 Когда COM вызывает управляемый код, значения HRESULT могут вызывать указанные ниже проблемы.  
  
-   Функции COM, возвращающие значения HRESULT меньше нуля (коды сбоев), создают исключения.  
  
-   Методы COM, регулярно возвращающие два или более разных кодов успешного выполнения, например <xref:Microsoft.VisualStudio.VSConstants.S_OK> и <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, невозможно различить.  
  
 Так как многие функции COM [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] возвращают значения HRESULT меньше нуля или различные коды успешного выполнения, сборки взаимодействия [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] были написаны так, чтобы сигнатуры методов сохранялись. Все методы взаимодействия [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] имеют тип `int` . Значения HRESULT передаются через уровень взаимодействия без изменения и без создания исключений.  
  
 Так как функция COM возвращает значение HRESULT в вызвавший ее управляемый метод, вызывающий метод должен проверить значение HRESULT и при необходимости создать исключения.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM  
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. Класс <xref:Microsoft.VisualStudio.ErrorHandler> содержит метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, который создает исключение COM в зависимости от переданного ему значения HRESULT.  
  
 По умолчанию метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда ему передается значение HRESULT меньше нуля. В случаях, когда такие значения HRESULT являются допустимыми и исключения создавать не нужно, в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> следует передать дополнительные значения HRESULT после их проверки. Если проверяемые значения HRESULT совпадают со значениями HRESULT, явно переданными в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не создается.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Класс содержит константы для общих значений HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK> и <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, и [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] значения HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> также предоставляет методы <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, которые соответствуют макросам SUCCEEDED и FAILED в COM.  
  
 Например, рассмотрим приведенный ниже вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> является допустимым возвращаемым значением, но любое другое значение HRESULT меньше нуля представляет ошибку.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Если имеется несколько допустимых возвращаемых значений, дополнительные значения HRESULT можно просто добавить в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода  
 Если исключений не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK> в вызвавшую его функцию COM. COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий недопустимый аргумент `null`, вызывает исключение <xref:System.ArgumentNullException>.  
  
 Если вы не знаете, какое именно исключение следует создать, но знаете, какое значение HRESULT нужно вернуть в COM, вы можете использовать метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> для создания соответствующего исключения. Такой подход работает и в случае с нестандартными ошибками, например <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. Метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> пытается сопоставить переданное ему значение HRESULT со строго типизированным исключением. Если это ему не удается, он создает универсальное исключение COM. Конечным результатом является то, что значение HRESULT, которое вы передали в <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> из управляемого кода, возвращается в вызвавшую этот код функцию COM.  
  
> [!NOTE]
>  Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.  
  
## <a name="see-also"></a>См. также  
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)   
 [Взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Практическое: сопоставление значений HRESULT и исключений](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Построение компонентов COM для взаимодействия](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)