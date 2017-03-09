---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
Пользовательский инструмент не может быть создан системой работы с проектами.  Запрашиваемый пользовательский инструмент не будет запущен, так как системе работы с проектами не удалось создать его экземпляр.  Убедитесь, что пользовательский инструмент правильно установлен и зарегистрирован.  
  
 Причиной этой ошибки может быть указание в свойстве `CustomTool` некоторого файла недопустимого имени пользовательского инструмента.  Также возможно, что файл проекта \(VBPROJ\/CSPROJ\) был отредактирован таким образом, что значение свойства `CustomTool` стало недопустимым.  Или, возможно, используется проект, разработанный на другом компьютере, на котором установлен пользовательский инструмент, который не установлен на данном компьютере.  Дополнительные сведения о свойстве `CustomTool` см. в разделе [File Properties](http://msdn.microsoft.com/ru-ru/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Причиной возникновения этой ошибки также может быть сбой при выполнении функции [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) для пользовательского инструмента.  Например, он не был зарегистрирован или отсутствует требуемая библиотека DLL.  
  
## См. также  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)