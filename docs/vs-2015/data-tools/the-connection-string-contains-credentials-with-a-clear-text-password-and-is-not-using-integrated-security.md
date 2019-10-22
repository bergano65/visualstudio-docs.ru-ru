---
title: Строка подключения содержит учетные данные с открытым текстовым паролем и не использует встроенную безопасность | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8fc2a428753e9650bb0dfebdb2bfdfdde10697a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672288"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную систему безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы хотите сохранить строку подключения к текущему файлу DBML и файлам конфигурации приложения с этой конфиденциальной информацией?  Нажмите кнопку Нет, чтобы сохранить строку подключения без конфиденциальной информации.

 При работе с подключениями к данным, которые содержат конфиденциальную информацию (пароли, которые включены в строку подключения), предоставляется опция сохранения строки подключения в файл DBML проекта и файл конфигурации приложения с или без конфиденциальной информации.

> [!WARNING]
> При явной установке свойства **Соединение** в окне **Настройки приложения** в значение **False** будет добавлен пароль в DBML-файл.

### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения с конфиденциальной информацией в параметрах приложения проекта

- Щелкните **Да**.

     Строка подключения сохраняется как параметр приложения. Строка подключения включает конфиденциальную информацию в обычный текст. В файле DBML отсутствует конфиденциальная информация.

### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения без конфиденциальной информации в параметрах приложения проекта

- Нажмите кнопку **Нет**.

     Строка подключения сохраняется как параметр приложения, но не включает пароль.

## <a name="see-also"></a>См. также раздел
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
