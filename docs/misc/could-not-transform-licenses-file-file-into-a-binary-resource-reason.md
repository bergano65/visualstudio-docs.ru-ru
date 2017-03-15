---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
Произошла ошибка в обработчике лицензий, который используется для преобразования LICX\-файлов в двоичные файлы ресурсов.  
  
 Причиной этой ошибки обычно является поврежденный LICX\-файл.  Например, возможно, что файл был открыт и изменен в текстовом редакторе.  
  
 При возникновении этой ошибки процесс построения завершается неудачей.  
  
### Чтобы исправить эту ошибку  
  
1.  Выберите проект в обозревателе решений.  
  
2.  В меню **Проект** выберите команду **Показать все файлы**.  
  
3.  В обозревателе решений откройте папку **Отладка**, вложенную в папку "obj".  
  
4.  Найдите файл "МоеПриложение.exe.licenses", где "МоеПриложение" — имя приложения Windows Forms.  
  
5.  Удалите этот файл и выполните построение решения еще раз.  
  
## См. также  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)