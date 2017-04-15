# ScriptX
Auxilia a adi��o de m�todos e vari�veis ao PascalScript

## Exemplo de uso

```delphi
type
  TDummy = class
  public
	[RegisterMethod]
    procedure MostraMsg(AMsg : string);
  end;

var LScript : IScriptX;
    LScriptContext : IScriptXContext;
begin
  LScript := TScriptX.Create;
  LScript.RegisterMethods(TDummy);
  LScriptContext := TScriptXContext.Create;
  LScript.SetContext(LScriptContext);
  LScriptContext.AddVariable(TScriptXVariable.New
  .SetName('LSomeString')
  .SetVariableType(vtString)
  .SetOnGetValue(
    procedure (var AValue : TValue)
    begin
      AValue := 'NOOB TEST';
    end));
  LScript.SetScript('begin MostraMsg(LSomeString); end.').Execute;
end;
```