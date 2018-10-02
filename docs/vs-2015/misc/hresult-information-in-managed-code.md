---
title: Информация HRESULT в управляемом коде | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558121"
---
# <a name="hresult-information-in-managed-code"></a>Информация HRESULT в управляемом коде
В процессе взаимодействия между управляемым кодом и моделью COM могут возникать проблемы, если возвращаются значения HRESULT.  
  
 В COM-интерфейсе возвращаемое значение HRESULT может выполнять следующие функции:  
  
-   Предоставлять сведения об ошибке (например, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
-   предоставлять сведения о состоянии нормального выполнения программы.  
  
 Когда COM вызывает управляемый код, значения HRESULT могут вызывать указанные ниже проблемы.  
  
-   Функции COM, возвращающие значения HRESULT меньше нуля (коды сбоев), создают исключения.  
  
-   Методы COM, регулярно возвращающие два или более разных кодов успешного выполнения, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK> или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, невозможно различить.  
  
 Так как многие [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] функций COM, возвращают значения HRESULT меньше нуля или различные коды успешного выполнения, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] были записаны сборки взаимодействия, чтобы сигнатуры методов сохранялись. Все [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] имеют методы взаимодействия `int` типа. Значения HRESULT передаются через уровень взаимодействия без изменения и без создания исключений.  
  
 Так как функция COM возвращает значение HRESULT в вызвавший ее управляемый метод, вызывающий метод должен проверить значение HRESULT и при необходимости создать исключения.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM  
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. <xref:Microsoft.VisualStudio.ErrorHandler> Класс содержит <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> переданного ему метод, который создает исключение COM, в зависимости от значения HRESULT.  
  
 По умолчанию <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда он передается значение HRESULT, которое имеет значение меньше нуля. В случаях, когда такие HRESULT являются допустимыми, и исключение не должно вызываться, должны быть переданы дополнительные значения HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> после проверки на значения. Если проверяемое значение HRESULT совпадают со значениями HRESULT, явно переданных <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не создается.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Класс содержит константы для общих значений HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK> и <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, и [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] значения HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> также предоставляет <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> методы, которые соответствуют макросы SUCCEEDED и FAILED в COM.  
  
 Например, рассмотрим следующий вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> является допустимым возвращаемым значением, но любое другое значение HRESULT меньше нуля представляет ошибку.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Если имеются несколько допустимых возвращаемых значений, дополнительные значения HRESULT можно просто добавить в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода  
 Если исключение не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK> функции COM, который вызвал ее. COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий недопустимый `null` создает исключение аргумента <xref:System.ArgumentNullException>.  
  
 Если нет уверенности, какие исключения, но вы знаете значение HRESULT нужно вернуть в COM, можно использовать <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> метод для создания соответствующего исключения. Это работает даже с нестандартными ошибками, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> пытается сопоставить значение HRESULT переданное ему со строго типизированным исключением. Если это ему не удается, он создает универсальное исключение COM. Конечным результатом является то, что значение HRESULT передается <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> из управляемого кода возвращается функции COM, который вызвал ее.  
  
> [!NOTE]
>  Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.  
  
## <a name="see-also"></a>См. также  
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)   
 [Взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Практическое: сопоставление значений HRESULT и исключений](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Построение компонентов COM для взаимодействия](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)