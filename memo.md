## 遅延静的束縛
selfは定義時に解決される。  
そのため、継承先で呼び出しても継承前の定義が返ってくる。  
これを解決するために、定義を遅らせる必要がある。  
それを可能にするのが、static::である。self部分をstaticに変える。