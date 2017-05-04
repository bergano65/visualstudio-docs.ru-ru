---
title: "Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "глобализация [разработка решений Office в Visual Studio], настройка пользовательского интерфейса"
  - "локализация [разработка решений Office в Visual Studio], настройка пользовательского интерфейса"
  - "MUI [разработка решений Office в Visual Studio]"
  - "многоязыковой пользовательский интерфейс [разработка решений Office в Visual Studio]"
  - "Office - приложения [разработка решений Office в Visual Studio], глобализация"
  - "Office - приложения [разработка решений Office в Visual Studio], локализация"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office
  Многоязыковый пользовательский интерфейс \(MUI\) — это функциональная возможность Microsoft Office, предоставляющая пользователю возможность изменения языка пользовательского интерфейса.  Например, пользователь, работающий в английском пользовательском интерфейсе, может сменить язык интерфейса на испанский.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Если приложение предназначено для тех, кто использует множество языков Office, можно добавить код, который будет автоматически изменять язык строк пользовательского интерфейса в соответствии с языком Office на компьютере пользователя \(если у пользователя установлены соответствующие ресурсы\).  
  
### Проверка текущих установок пользовательского интерфейса Office  
  
1.  Воспользуйтесь свойством <xref:System.Threading.Thread.CurrentUICulture%2A> текущего потока.  Установите язык строк пользовательского интерфейса в соответствии с языком, используемым версией Office, выполняющейся в текущий момент на компьютере пользователя.  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## См. также  
 [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)  
  
  