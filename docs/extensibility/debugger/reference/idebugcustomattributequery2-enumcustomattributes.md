---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf7647371246e74ba99bc79233007539e03f9782
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Возвращает перечислитель для всех настраиваемых атрибутов, вложенные в это поле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) объект, представляющий список настраиваемых атрибутов; в противном случае возвращает значение null, если нет никаких настраиваемых атрибутов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает S_OK или S_FALSE, если нет никаких настраиваемых атрибутов для этого поля. В противном случае возвращается код ошибки;  
  
## <a name="remarks"></a>Примечания  
 Это поле может иметь несколько пользовательских атрибутов.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)