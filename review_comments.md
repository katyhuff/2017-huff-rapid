
# Reviewers' comments:

## Reviewer 1: 

The paper is about nuclide transport models implemented in a nuclear fuel cycle simulation model. It is in general written in an understandable manner, but lacks some rigor.

(1) Introduction gives a brief review for related previous works. This is a very limited literature review, and touches only how nuclear fuel cycle simulation models currently available implement repository components. It is informative, but because the present paper is about nuclide transport models, there must be a comprehensive review for radionuclide transport models that were previously developed, by focusing on adaptability of those models into fuel cycle models. Actually some of the models described in this paper were already reported somewhere else. These should be fairly mentioned and referred to.

(2) Figure 1: Is the groundwater flowing in the vertical (z) direction upward? In reality, this is a rare situation. If water flows vertically, how would adjacent packages interact each other?

(3) While Section 2.1 is about "Time Stepping Algorithm," it is not clear how the time step has been set for processes with largely different mass transfer rates?

(4) In Eq. (3), function f(r) is used without definition.

(5) In Eq. (8), the total volume is assumed constant. In reality, when degradation such as corrosion or bentonite swelling due to imbibition of water occurs, the total volume changes. As an assumption in the model, it is OK, but there must be some discussion about validity of this assumption.

(6) In the solubility-limited model, there seems to be no consideration for generation of precipitate of a nuclide. It may be Ok for a single nuclide case, but when a multi-member decay chain is considered, due to decay from the precursor, within a certain region, there can be more mass of the decay daughter than what the water phase can contain, resulting in precipitation of the daughter. This occupies a certain volume of the space. The current model does not seem to be valid for such situation. Again, there should be careful literature survey for previous works.

(7) Line 193 in Page 15 should be a title of subsection.

(8) Eq. (40), the second term in the left side, c should be C?

(9) Numerical results are shown for no sorption case. In the no-sorption case, radionuclides tend to be transported faster, so that in general numerical simulation is easier than cases with strong sorption, because with strong sorption concentration gradients become steeper, for which more finer mesh division is necessary. If simulation is attempted for a multi-member decay chain with sorption, it would be even more challenging. Can the present code handle such situation?



## Reviewer 2: 

The paper presents a computational module CYDER to be (or already is) integrated in the CYCLUS fuel cycle analysis code. CYDER allows to evaluate the impact of the fuel cycle on the final disposal options. In its current state, I believe the paper absolutely not ready for publication in a peer-reviewed journal. This is work-in-progress that can find a place in the right scientific conference for an oral or poster presentation.

### General comments

- The motivation can be more elaborated. Why is this so important? See first detailed comment.
- The models mentioned and used are not referenced and are not well-explained. What are the different hypotheses behind the models?
- A paper like this should include a decent comparison, code-to-code or code-to-experiments.


### Detailed comments

- The abstract and introduction mention the necessity of including repository performance metrics into (dynamic) nuclear fuel cycle similators. However, these metrics themselves and their link with decision-making at the level of fuel cycle options are not elaborated. There is a need to further motivate 1) the need for indicators other than classical ones (mass, volumes, radiotoxicity, heat production, and required gallery length or repository footprint) and 2) the added value of incorporating the geosphere and biosphere transport into a fuel cycle tool.
- p.4: The author mentions (line 57) that an implicit time stepping method is used. However, it is totally unclear from section 2 where and how this is implemented. If it is an implicit method, it means that it uses information at the current time step (which is not available), hence an iteration (typically non-linear) is required. Where is this explained? How is the non-linear problem solved? As it is described now, I cannot even judge on the convergence of the time stepping method. What is the limit on the maximum time-step to guarantee convergence?
- p.6: What is the meaning of equation (3)? How can this be equal to zero without any or both of the factors f(r) and C_j(r) being zero?
- p.10, formula above line 150: how can f_n be [kg]? shouldn't it be [1/s]?
- p.10, 11: define $\theta$
- p.14: The effectiveness of a solubility limit depends on its value and the predicted concentrations (or mass & pore volume) at the considered location. For correct representation of real systems, the dimension of the model plays an important role and usually 2D models or 1D radial models (for cylindrical galleries) are applied as a minimum.
- p.16: Host rocks (especially clays, such as in ref. [19]) are often selected such that solute transport is governed by diffusion rather than advection. What is the implication for the dispersion model (DM) when q -> 0?
- p.29 and further. The single effect parametric analyses is interesting but needs to be further elaborated with respect to conceptual model and assumptions. It demonstrates that the simplified CYDER model can handle linear sorption and solubility limits, but in general this section would benefit a lot from a benchmark exercise using more representative parameter values.
- The conclusions claim that "agreement between CYDER and a more detailed stand-alone model was demonstrated". However, it needs to be clear that the agreement is restricted to general model response behavior, and that the model is not yet numerically verified.





