#Tracking Channel

## Structure Diagram
```dot
digraph G
{
  node [shape = record];
  svctrl [label = "{ struct sv_ctrl | ... }"];

  trkchan [label = "{ struct trk_channel | ... }"];
  bitsync [label = "{ struct trk_bitsync | ... }"];

  acqchan [label = "{ struct acq_channel | ... }"];
  acqmode [label = "{ struct acq_searchmode | ... }"];
  acqcfg [label = "{ struct acq_searchcfg | ... }"];

  acqchan -> svctrl -> acqchan;
  trkchan -> svctrl -> trkchan;
  svctrl -> acqmode -> acqcfg;
  trkchan -> bitsync;
}
```

## Declaration
```c
struct trk_channel
{
};


struct trk_channel *trkchan_alloc(void);
void trkchan_dealloc(struct trk_channel *trkchan);
void trkchan_gc(void);

void trkchan_stop(struct trk_channel *trkchan);

```
