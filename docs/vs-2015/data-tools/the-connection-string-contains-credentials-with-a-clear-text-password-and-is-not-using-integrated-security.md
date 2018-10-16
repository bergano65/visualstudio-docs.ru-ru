---
title: Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную безопасность | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1ec13cab1b8c41225cb1934740b8dd3e7f59ac0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230880"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную систему безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Вы хотите сохранить строку подключения к текущему файлу DBML и файлам конфигурации приложения с этой конфиденциальной информацией?  Нажмите кнопку Нет, чтобы сохранить строку подключения без конфиденциальной информации.  
  
 При работе с подключениями к данным, которые содержат конфиденциальную информацию (пароли, которые включены в строку подключения), предоставляется опция сохранения строки подключения в файл DBML проекта и файл конфигурации приложения с или без конфиденциальной информации.  
  
> [!WARNING]
>  Явная установка **подключения** свойства **параметры приложения** свойства **False** добавит пароль в DBML-файл.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения с конфиденциальной информацией в параметрах приложения проекта  
  
-   Нажмите кнопку **Да**.  
  
     Строка подключения сохраняется как параметр приложения. Строка подключения включает конфиденциальную информацию в обычный текст. В файле DBML отсутствует конфиденциальная информация.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения без конфиденциальной информации в параметрах приложения проекта  
  
-   Нажмите кнопку **Нет**.  
  
     Строка подключения сохраняется как параметр приложения, но не включает пароль.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

