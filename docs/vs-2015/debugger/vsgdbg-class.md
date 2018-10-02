---
title: Класс VsgDbg | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 927990cb8fb21dfeaf25a681cfb0a222ecc3c8ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557633"
---
# <a name="vsgdbg-class"></a>Класс VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [класс VsgDbg](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-class).  
  
Представляет интерфейс для управления программными компонент диагностики графики в приложении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Участники  
 `VsgDbg` Класс поддерживает следующие члены.  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (конструктор)](../debugger/vsgdbg-vsgdbg-constructor.md)|Создает экземпляр класса `VsgDbg` класса и при необходимости подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[VsgDbg::~VsgDbg (деструктор)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Уничтожает экземпляр `VsgDbg` класса.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Добавляет пользовательское сообщение диагностики графики HUD (головной дисплей).|  
|[BeginCapture](../debugger/begincapture.md)|Начинается интервал захвата, будут заканчиваться `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Захватывает оставшуюся часть текущего кадра в файл журнала графики.|  
|[Copy (программный захват)](../debugger/copy-programmatic-capture.md)|Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.|  
|[EndCapture](../debugger/endcapture.md)|Завершает интервал захвата, начатый функцией `BeginCapture`.|  
|[Init](../debugger/init.md)|Подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[ToggleHUD](../debugger/togglehud.md)|Переключает наложение HUD диагностики графики, включить или отключить.|  
|[UnInit](../debugger/uninit.md)|Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.|  
  
## <a name="remarks"></a>Примечания  
 `VsgDbg` Класс представляет интерфейс, который можно использовать для управления функциями диагностики графики программными средствами. Можно использовать некоторые возможности, даже в том случае, если вы не активно захвата и записи данных графики; Сюда входят `AddMessage` функция-член и `ToggleHUD` функция-член. Другие функции-члены Подготовка компонент в приложении диагностики графики для запуска или остановки active захвата графических данных либо должен вызываться, пока приложение активно захват и запись сведений графики файла журнала графики.



