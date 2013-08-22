#Tracking Channel

## Structure Diagram
```dot
digraph G
{
  node [shape = record];
  trkchan [label = "{ struct trk_channel | ... }"];
  acqchan [label = "{ struct acq_channel | ... }"];
  acqmode [label = "{ struct acq_searchmode | ... }"];
  acqcfg [label = "{ struct acq_searchcfg | ... }"];
  
  sig [label = "{ struct sv_signal | ... }"];
  bitsync [label = "{ struct trk_bitsync | ... }"];
  trkchan -> acqchan -> sig;
  acqchan -> trkchan -> sig;
  acqchan -> acqmode -> acqcfg;
  trkchan -> bitsync;
}
```

## Declaration
```c
struct trk_channel
{
};

struct trk_channel *trkchan_alloc(void);
void trkchan_dealloc(struct trk_channel *trk);
void trkchan_gc(void);
```
