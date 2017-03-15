---
title: "Ошибка MSBuild MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB8031
MSB8031  
  
 Для использования кодирования MBCS в проектах MFC необходимо загрузить и установить дополнительные библиотеки.  
  
 Версии многобайтовой кодировки MFC DLL не включаются в Visual Studio, но они доступны в дополнительном компоненте многобайтовой кодировки DLL MFC, которую можно загрузить, если вы клиент Visual Studio.  Если не установить дополнительный компонент и попытаться собрать проект MFC, использующий многобайтовую кодировку, компоновщик не найдет библиотеки DLL и сборка завершится ошибкой.  
  
### Чтобы исправить эту ошибку  
  
1.  [Загрузите дополнительный компонент библиотеки DLL Microsoft Foundation Class \(MFC\) с поддержкой многобайтовой кодировки \(MBCS\)](http://go.microsoft.com/fwlink/?LinkId=299009) в центре загрузки MSDN или если это удобно сделать, преобразуйте проект в кодировку юникод.  
  
## См. также  
 [Надстройка DLL MBCS MFC](/visual-cpp/mfc/mfc-mbcs-dll-add-on)