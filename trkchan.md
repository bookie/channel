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


void trkchan_init(unsigned chansize);
struct trk_channel *trkchan_deploy(struct sv_ctrl *svctrl);
void trkchan_kill(struct trk_channel *trkchan);

void trkchan_gc(void);


```
