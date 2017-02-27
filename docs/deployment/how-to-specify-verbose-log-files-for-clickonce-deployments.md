---
title: "Практическое руководство. Указание подробных файлов журнала для развертывания ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "развертывание ClickOnce, ведение журналов"
  - "журналы, развертывание ClickOnce"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# Практическое руководство. Указание подробных файлов журнала для развертывания ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] поддерживает файлы журналов действий для всех развертываний.  В этих журналах содержатся подробные сведения, относящиеся к установке, инициализации и удалению развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Чтобы настроить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] на запись более подробной информации в файлы журнала, используйте редактор реестра \(**regedit.exe**\) для указания уровня детализации.  
  
> [!CAUTION]
>  Неправильная работа с редактором реестра может привести к возникновению серьезных проблем, которые могут потребовать переустановки операционной системы.  Ответственность за использование редактора реестра лежит на пользователе.  
  
 В следующей процедуре описывается процесс указания уровня детализации для файлов журнала [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] текущего пользователя.  Чтобы понизить уровень детализации, удалите это значение реестра.  
  
### Указание подробных файлов журнала  
  
1.  Откройте программу **Regedit.exe**.  
  
2.  Перейдите к узлу `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  При необходимости создайте новое строковое значение с именем `LogVerbosityLevel`.  
  
4.  Установите значение `LogVerbosityLevel` равным `1`.  
  
## См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)