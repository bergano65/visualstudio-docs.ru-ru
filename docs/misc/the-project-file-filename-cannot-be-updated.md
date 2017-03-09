---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
Предпринимается попытка открыть проект, созданный в ранней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Формат проекта необходимо обновить, но этого сделать не удается, так как файл проекта \(с расширением VBPROJ\) либо имеет атрибут "Только чтение", либо находится под контролем системы управления версиями и в данный момент заблокирован другим пользователем.  
  
### Чтобы исправить эту ошибку  
  
1.  В обозревателе файла найдите указанный файл проекта.  
  
2.  В меню **File** выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства** снимите флажок атрибута **Только чтение**.  
  
 Если файл контролируется системой управления версиями и заблокирован другим пользователем, дождитесь его освобождения и извлеките файл на локальный компьютер.  
  
## См. также  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)