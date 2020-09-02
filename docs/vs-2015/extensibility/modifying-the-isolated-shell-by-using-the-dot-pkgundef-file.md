---
title: Изменение изолированной оболочки с помощью. Файл Pkgundef | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538398"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Изменение изолированной оболочки с помощью файла .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете изменить файл pkgundef, чтобы исключить указанные записи реестра из изолированного приложения оболочки. Как правило, при первом запуске приложения на компьютере оболочка Visual Studio копирует существующие записи реестра Visual Studio в корневой раздел реестра для приложения. Сюда входят все ссылки на установленные пакеты VSPackage.  
  
 Чтобы исключить определенную запись реестра из изолированного приложения оболочки, добавьте в файл Application. pkgundef ключ пакета, за которым следует запись. Ключи и записи представляются точно так же, как в файле pkgdef; то есть, AS [$RootKey $] или [$RootKey $ \\ *subkey*] и "*entry*" =*значение*, где *подраздел* — это подраздел для влияния, *запись* — это Удаляемая запись, а *значение* — `""` либо `dword:00000000` .  
  
 Чтобы исключить несколько записей из раздела реестра, просто Вычислите ключ один раз, за которым следует строка для каждой исключаемой записи.  
  
 Чтобы исключить весь раздел реестра из изолированного приложения оболочки, добавьте ключ в файл Application. pkgundef, но не указывайте записи реестра для этого раздела.  
  
 Можно добавить комментарии в файл pkgundef. Однострочный комментарий должен содержать две косые черты в качестве первых двух символов.  
  
 Например, чтобы удалить команду **подключиться к базе данных** и **подключиться для обслуживания команд r** в меню **Сервис** , можно раскомментировать строку:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 и добавьте строку:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 в файл. pkgundef приложения.  
  
## <a name="see-also"></a>См. также:  
 [Идентификаторы GUID пакетов компонентов Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)
